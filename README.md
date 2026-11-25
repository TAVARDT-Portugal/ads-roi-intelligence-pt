# Inteligência e Modelação Matemática de ROI em Campanhas Pagas

[![Calculadora ROI](https://img.shields.io/badge/TAVARDT-Calculadora%20ROI-5b3cf5.svg)](https://tools.tavardt.com/pt/calculadora-roi-campanhas-pagas/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Mecanismo matemático determinístico para análise de ROAS, ROI e projeções de escala não lineares com fatores de retornos decrescentes em tráfego pago.

A ferramenta equipa engenheiros de receita, gestores de performance e analistas de dados com modelação econométrica rigorosa para simular a alocação de capital sem assumir retornos lineares. Desenvolvido sem dependências externas, o toolkit executa de forma nativa em Python e JavaScript.

***

## Fundamentos Algorítmicos e Modelação Matemática

Projeções puramente lineares em campanhas publicitárias resultam em alocações ineficientes de capital e estimativas financeiras enganadoras. Na realidade dos leilões de tráfego, o crescimento orçamental gera saturação de audiências, desgaste criativo e aumento sistemático dos custos marginais.

* **Cálculo de ROAS Base**: Relação direta entre receita bruta e investimento realizado (`revenue / spend`), mensurando a eficiência imediata.
* **Cálculo de ROI Base**: Rendimento percentual líquido sobre o capital investido (`((revenue - spend) / spend) * 100`), calculando a rendibilidade real.
* **Projeção de Escala Não Linear**: Aplicação do expoente `(decay_factor - 1)` sobre a razão de investimento `(target_spend / current_spend)` para antecipar a quebra no ROAS.
* **Perda de Eficiência Marginal**: Cálculo da percentagem de perda de rendimento associada à progressão para um patamar de investimento superior.
* **Arquitetura Isomórfica Dupla**: Fórmulas matemáticas estritamente idênticas implementadas na biblioteca padrão Python (`roi_engine.py`) e em JavaScript puro (`calculator.js`).

***

## Matriz de Métricas e Modelação Matemática

<table>
  <thead>
    <tr>
      <th align="left">Métrica / Parâmetro</th>
      <th align="left">Fórmula Algorítmica</th>
      <th align="left">Comportamento Matemático</th>
      <th align="left">Utilidade Estratégica na Tomada de Decisão</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>ROAS Base</strong></td>
      <td><code>revenue / spend</code></td>
      <td>Quociente linear direto arredondado a duas casas decimais.</td>
      <td>Avalia a eficiência imediata gerada por cada euro aplicado em campanhas.</td>
    </tr>
    <tr>
      <td><strong>ROI Base</strong></td>
      <td><code>((revenue - spend) / spend) * 100</code></td>
      <td>Margem percentual líquida obtida após cobertura total dos custos.</td>
      <td>Assegura a rentabilidade líquida do capital após amortização do investimento.</td>
    </tr>
    <tr>
      <td><strong>Razão de Escala</strong></td>
      <td><code>target_spend / current_spend</code></td>
      <td>Multiplicador de expansão orçamental nos testes de escala.</td>
      <td>Mede a magnitude relativa do aumento de capital inserido nos leilões.</td>
    </tr>
    <tr>
      <td><strong>ROAS Projetado</strong></td>
      <td><code>current_roas * (spend_ratio ** (decay_factor - 1))</code></td>
      <td>Decaimento por lei de potência induzido pela saturação de mercado.</td>
      <td>Evita sobrestimações de volume de negócio durante fases agressivas de expansão.</td>
    </tr>
    <tr>
      <td><strong>Receita Projetada</strong></td>
      <td><code>target_spend * projected_roas</code></td>
      <td>Faturação bruta esperada sob a curva de retornos decrescentes.</td>
      <td>Determina se a receita adicional cobre os custos estruturais complementares.</td>
    </tr>
    <tr>
      <td><strong>Perda de Eficiência</strong></td>
      <td><code>(1 - (projected_roas / current_roas)) * 100</code></td>
      <td>Redução percentual de eficácia marginal com o aumento do orçamento.</td>
      <td>Quantifica a penalização de eficiência exigida para capturar volume adicional.</td>
    </tr>
  </tbody>
</table>

***

## Instalação e Guia de Execução Rápida

Requer Python 3.8 ou superior utilizando unicamente bibliotecas padrão (`sys`, `json`, `argparse`). Não são necessárias instalações externas via pip.

Clone o repositório e execute a análise inicial no terminal:

```bash
git clone https://github.com/TAVARDT-Portugal/ads-roi-intelligence-pt.git
cd ads-roi-intelligence-pt
python roi_engine.py -s 10000 -r 50000 -ts 25000
```

Para exportar os resultados em formato estruturado JSON:

```bash
python roi_engine.py -s 10000 -r 50000 -ts 25000 -j
```

Ajuste o fator de decaimento para calibrar cenários com saturação de tráfego acelerada:

```bash
python roi_engine.py -s 10000 -r 50000 -ts 30000 -d 0.78
```

Para ambientes Node.js ou execução no browser, utilize o ficheiro `calculator.js`:

```javascript
const ROI_Calculator = require('./calculator.js');

const base = ROI_Calculator.calculateBaseMetrics(10000, 50000);
console.log('ROAS Base:', base.roas, 'ROI Base:', base.roi);

const projecao = ROI_Calculator.projectScale(10000, 25000, base.roas, 0.85);
console.log('ROAS Projetado:', projecao.projectedROAS);
console.log('Perda de Eficiência:', projecao.efficiencyLoss + '%');
```

Exemplo de payload estruturado em JSON:

```json
{
  "currency": "EUR",
  "current_spend": 10000.0,
  "current_revenue": 50000.0,
  "base_metrics": {
    "roas": 5.0,
    "roi": 400.0
  },
  "scaling_projection": {
    "target_spend": 25000.0,
    "decay_factor": 0.85,
    "projection": {
      "projected_roas": 4.36,
      "projected_revenue": 109000.0,
      "efficiency_loss": 12.8
    }
  }
}
```

***

## Perguntas Frequentes (FAQ Técnico)

### De que forma o fator de decaimento modela os retornos decrescentes na escala de campanhas?
O fator de decaimento (`-d`, valor padrão 0.85) opera como expoente de potência `(decay_factor - 1)` aplicado à taxa de expansão orçamental. À medida que o orçamento cresce, as impressões adicionais enfrentam saturação e custos marginais mais elevados, reduzindo deterministicamente o ROAS projetado.

### Quais são as distinções operacionais entre o CLI Python e o módulo JavaScript?
Ambas as variantes processam rigorosamente as mesmas fórmulas matemáticas e tolerâncias de arredondamento. O CLI Python (`roi_engine.py`) destina-se a execuções em terminal e automações de dados, enquanto `calculator.js` serve diretamente aplicações Node.js e dashboards de monitorização no cliente.

### Como pode a saída JSON ser integrada em infraestruturas analíticas e pipelines de BI?
Ao passar o parâmetro `-j` no terminal, o motor produz exclusivamente texto JSON válido na saída padrão. Essa estrutura pode ser consumida diretamente por comandos utilitários como jq ou carregada em data warehouses através de tarefas de ingestão contínua.

### Por que razão a ferramenta dispensa bibliotecas externas ou chamadas a APIs remotas?
A ausência de bibliotecas externas assegura imunidade contra falhas de dependência na cadeia de distribuição de software e tempos de processamento sub-milissegundo. Adicionalmente, permite o funcionamento em servidores isolados sem conectividade externa.

### Como é que a métrica de perda de eficiência marginal protege a rentabilidade das campanhas?
A perda de eficiência marginal demonstra a degradação percentual entre o ROAS de partida e o ROAS estimado. Se a compressão calculada situar o rendimento abaixo do limiar de rentabilidade da operação, os gestores podem congelar a expansão antes de incorrerem em perdas financeiras.

***

## Consultoria em Engenharia de Receita

Para otimização de orçamentos publicitários, modelação econométrica e escala de aquisição B2B em Portugal, consulte os especialistas da **TAVARDT Portugal**.

***

## Links Úteis

* **Portal Corporativo:** https://ag.tavardt.com/pt/
* **Suíte de Diagnósticos:** https://tools.tavardt.com/pt/
* **Contacto Técnico:** https://ag.tavardt.com/pt/contacto/

***

### Licença
Distribuído sob a Licença MIT.

***

© 2026 TAVARDT. Todos os direitos reservados.
