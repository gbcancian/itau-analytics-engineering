# Case Técnico: Engenharia de Analytics Jr - Cyber Security (Itaú)

## Sobre o Projeto
Este projeto foi desenvolvido como parte do processo seletivo para a vaga de **Analista de Engenharia de Analytics Jr - Cyber Security (833516)** no Itaú Unibanco. 

O objetivo principal é analisar uma base de dados de vulnerabilidades tecnológicas, tratar inconsistências, modelar os dados e extrair *insights* executivos para apoiar a tomada de decisão da liderança na mitigação de riscos (focando na priorização de ativos e efetividade do processo de correção).

## Arquitetura de Dados (Medalhão)
O pipeline de dados foi construído adotando a Arquitetura Medalhão para garantir a rastreabilidade e a qualidade da informação:

*   ** Camada Bronze:** Arquivos originais `.csv` (`ativos.csv` e `vulnerabilidades.csv`).
*   ** Camada Silver:** Dados tratados, padronizados (correção de datas, remoção de ativos inexistentes como o `A9999`) e guardados em formato `.parquet` para otimização de leitura.
*   ** Camada Gold:** Dados consolidados (cruzamento de vulnerabilidades com a base de ativos), com novas métricas calculadas (ex: `tempo_correcao_dias`), exportados em `.csv` para consumo direto no Dashboard Executivo.

## 📁 Estrutura de Ficheiros e Notebooks

O processo de ETL e Análise Exploratória está dividido em três *Jupyter Notebooks* sequenciais:

1.  **`01_data_quality.ipynb`:** Focado na avaliação descritiva dos dados brutos, identificação de valores nulos, formatos de datas inválidos e inconsistências lógicas (ex: datas de correção anteriores à abertura).
2.  **`02_data_preparation.ipynb`:** Aplicação das regras de negócio e higienização. Padronização de valores categóricos (Severidade, Origem), tratamento de datas e exportação para a camada Silver.
3.  **`03_data_analytics.ipynb`:** Análise de negócio para responder às perguntas da gestão. Geração das métricas de exposição ao risco, tempo mediano de correção e ranqueamento de ativos críticos. Geração da camada Gold.

##  Entregáveis Finais
Além dos *notebooks* de engenharia, este *case* inclui:
*   **Dashboard Executivo (Looker Studio):** Painel interativo para monitorização contínua do *backlog* de segurança. Link: https://datastudio.google.com/s/siTA9kvf4Gk
*   **Apresentação Executiva (PDF):** Relatório focado na priorização do risco e recomendações estratégicas para a direção.

Todos esses documentos estão salvos dentro da pasta docs, para ter acesso aos filtros do dashboard abra pelo link.