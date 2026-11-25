# Inteligência e Modelação de ROI em Campanhas Pagas

[![Calculadora ROI](https://img.shields.io/badge/TAVARDT-Calculadora%20ROI-5b3cf5.svg)](https://tools.tavardt.com/pt/calculadora-roi-campanhas-pagas/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Modelação matemática para análise de ROAS, ROI e projeções de escala com retornos decrescentes para investimentos empresariais em publicidade digital.

***

## Modelação Matematica e Metricas

* **ROAS Base**: Relacao direta entre faturacao gerada e investimento publicitario.
* **ROI Base**: Retorno liquido sobre o capital investido em percentagem.
* **Projecao de Escala com Retornos Decrescentes**: Coeficiente de decaimento marginal (padrao 0.85) que prevê a perda de eficiencia a medida que o orçamento e aumentado.
* **Formatos de Saida**: Relatorio formatado em terminal ou saída estruturada em JSON para pipelines de analytics.

***

## Instalação e Execucao

Requer Python 3.8 ou superior sem dependencias externas.

```bash
git clone https://github.com/TAVARDT-Portugal/ads-roi-intelligence-pt.git
cd ads-roi-intelligence-pt
python roi_engine.py -spend 10000 -revenue 50000 -target-spend 25000
```

Para gerar a saída em formato JSON:

```bash
python roi_engine.py -spend 10000 -revenue 50000 -target-spend 25000 -json
```

***

## Consultoria em Desempenho e Receita

Para auditorias de investimento publicitario e otimizacao de escala em Portugal, contacte os especialistas da **TAVARDT Portugal**.

***

## Links Úteis

* **Portal Corporativo:** https://ag.tavardt.com/pt/
* **Suíte de Diagnósticos:** https://tools.tavardt.com/pt/
* **Contacto Técnico:** https://ag.tavardt.com/pt/contacto/

***

### Licença
Distribuído sob a Licença MIT.

***

© 2026 TAVARDT Portugal. Todos os direitos reservados. Soberania e Defesa de Infraestrutura.
