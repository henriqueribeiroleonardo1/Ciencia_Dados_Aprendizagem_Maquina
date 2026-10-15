<img src="assets/logo-udf.jpg" alt="UDF Centro Universitário" width="230">

**Profa. Kadidja Valéria | UDF**  
Ciência de Dados e Aprendizado de Máquina · Sistemas de Informação · 2026.2

# Módulo IV — Aprendizado de Máquina (exercícios)

Registro das atividades de introdução ao Machine Learning e de aprendizado supervisionado. As respostas são minhas e os números vêm dos notebooks que executei, com dados sintéticos fornecidos pela disciplina.

## Identificação

- Estudante: **Henrique Ribeiro Leonardo**
- Turma: **Sistemas de Informação — 2026.2**

## Atividades

| Arquivo | Entregável |
| --- | --- |
| [01-aula1-conceitos.md](01-aula1-conceitos.md) | Quadro comparativo e classificação justificada de sete problemas |
| [02-pbl-biblioteca.md](02-pbl-biblioteca.md) | Canvas da investigação (Biblioteca em Foco) |
| [03-aula2-laboratorio.md](03-aula2-laboratorio.md) | Registro do modelo, métricas, erros e experimentos em Python |
| [04-pbl-permanencia.md](04-pbl-permanencia.md) | Proposta de apoio à permanência, com avaliação e limites |
| [05-revisao.md](05-revisao.md) | Respostas individuais às 12 questões de revisão |
| [06-autoavaliacao.md](06-autoavaliacao.md) | Checklist, reflexão e ferramentas usadas |
| [07-aplicacao-tcc-rag.md](07-aplicacao-tcc-rag.md) | Aplicação ao meu TCC: roteador de perguntas para um assistente RAG local |

## Arquivos

| Caminho | O que é |
| --- | --- |
| [notebooks/laboratorio-henrique.ipynb](notebooks/laboratorio-henrique.ipynb) | Minha execução do laboratório (árvore de decisão, experimentos e regressão), com saídas |
| [notebooks/rag-roteador-henrique.ipynb](notebooks/rag-roteador-henrique.ipynb) | Experimento da atividade 07, com saídas |
| [notebooks/laboratorio.ipynb](notebooks/laboratorio.ipynb) | Notebook didático original da professora |
| `notebooks/resultados_*.json` | Números calculados em cada execução |
| [dados/educacionais-sinteticos.csv](dados/educacionais-sinteticos.csv) | CSV sintético da disciplina (600 registros) |
| [dados/perguntas_rag_sinteticas.csv](dados/perguntas_rag_sinteticas.csv) | Perguntas sintéticas geradas para a atividade 07 |
| `assets/` | Logomarca e gráficos gerados nos notebooks |

## Resumo dos resultados

| Experimento | Modelo escolhido no treino | Resultado no teste | Referência |
| --- | --- | --- | --- |
| Evasão (classificação) | Árvore, `max_depth=4`, `min_samples_leaf=40` | Acurácia 0,780; sensibilidade 0,770 | 0,593 |
| Empréstimos (regressão) | Regressão linear com os dois atributos | MAE 28,59; R² 0,877 | MAE 84,73 |
| Roteador do TCC (classificação, 5 classes) | Naive Bayes com TF-IDF de palavras | Acurácia 0,900; F1 macro 0,899 | 0,205 |

**Todos os dados são sintéticos. Não representam estudantes nem documentos reais.**

## Situação das entregas

- [x] Aula 1: quadro comparativo e problemas justificados.
- [x] PBL Biblioteca em Foco.
- [x] Aula 2: notebook e relatório.
- [x] PBL Apoio à Permanência.
- [x] Revisão e autoavaliação.
- [x] Aplicação ao TCC.

## Uso de IA

Usei um assistente de IA (Claude, da Anthropic) para apoiar a redação e a montagem dos notebooks. Executei os notebooks, conferi os cálculos e sou responsável pelo conteúdo.

## Fonte da atividade

Material do estudante do Módulo IV — Aprendizado de Máquina. Profa. Kadidja Valéria, UDF, 2026.
