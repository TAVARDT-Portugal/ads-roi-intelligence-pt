# Inteligência e Modelação de ROI em Campanhas Pagas | TAVARDT Portugal

[![Calculadora ROI](https://img.shields.io/badge/TAVARDT-Calculadora%20ROI-5b3cf5.svg)](https://tools.tavardt.com/pt/calculadora-roi-campanhas-pagas/)
[![Jurisdicao](https://img.shields.io/badge/Jurisdicao-Portugal-00C853.svg)](https://ag.tavardt.com/pt/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)

Modelação matemática para análise de ROAS, ROI e projeções de escala com retornos decrescentes para investimentos empresariais em publicidade digital.

Desenvolvido e mantido pela divisao de engenharia de receita e desempenho digital da **[TAVARDT Portugal](https://ag.tavardt.com/pt/)**.

---

## Modelação Matematica e Metricas

* **ROAS Base**: Relacao direta entre faturacao gerada e investimento publicitario.
* **ROI Base**: Retorno liquido sobre o capital investido em percentagem.
* **Projecao de Escala com Retornos Decrescentes**: Coeficiente de decaimento marginal (padrao 0.85) que prevê a perda de eficiencia a medida que o orcamento e aumentado.
* **Formatos de Saida**: Relatorio formatado em terminal ou saida estruturada em JSON para pipelines de analytics.

---

## Instalacao e Execucao

Requer Python 3.8 ou superior sem dependencias externas.

```bash
git clone https://github.com/TAVARDT-Portugal/ads-roi-intelligence-pt.git
cd ads-roi-intelligence-pt
python roi_engine.py --spend 10000 --revenue 50000 --target-spend 25000
```

Para gerar a saida em formato JSON:

```bash
python roi_engine.py --spend 10000 --revenue 50000 --target-spend 25000 --json
```

---

## Calculadora Interativa na Web

Para simulacoes graficas avancadas de campanhas empresariais, utilize a ferramenta oficial:

* **[Calculadora de ROI de Campanhas Pagas](https://tools.tavardt.com/pt/calculadora-roi-campanhas-pagas/)**
* **[Portal Corporativo TAVARDT Portugal](https://ag.tavardt.com/pt/)**

---

## Consultoria em Desempenho e Receita

Para auditorias de investimento publicitario e otimizacao de escala em Portugal, contacte os especialistas da **[TAVARDT Portugal](https://ag.tavardt.com/pt/contato/)**.
