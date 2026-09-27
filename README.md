# Identificação de Operadores Ineficientes - CallMeMaybe

Este projeto de análise de dados visa diagnosticar a ineficiência na base de operadores de telefonia virtual (VoIP) de uma empresa B2B, a CallMeMaybe. O objetivo central é fornecer um diagnóstico estruturado para a liderança de operações poder aplicar treinamentos direcionados, ajustar a distribuição de chamadas, melhorar o SLA de atendimento e reduzir o churn de clientes.

## Tecnologias e Bibliotecas Utilizadas
- **Linguagem:** Python
- **Manipulação de Dados:** Pandas, NumPy
- **Visualização:** Matplotlib, Seaborn
- **Estatística:** SciPy (Testes de Mann-Whitney U e Kruskal-Wallis)
- **Exportação:** Dados estruturados para Dashboard interativo no Tableau

## Funcionalidades e Etapas da Análise
- **Preparação e Limpeza de Dados:** Unificação de bases de clientes e chamadas (merge), tratamento de valores ausentes e remoção cirúrgica de outliers utilizando o limite do percentil 99 ajustado por direção da chamada.
- **Criação de Métricas e Perfilamento:** Engenharia de features para calcular o tempo de espera (*waiting_time*) e classificação dos 1.092 operadores em perfis de atuação (Ativo/Outbound, Receptivo/Inbound e Misto) baseada no comportamento histórico.
- **Diagnóstico de Ineficiência:** Aplicação rigorosa de regras de negócio para sinalizar operadores com alta taxa de abandono, longo tempo de espera (isolando apenas chamadas externas) e ociosidade no volume de chamadas ativas (outbound).
- **Testes de Hipóteses:** Execução de testes estatísticos para validar a diferença no tempo de espera entre chamadas internas/externas e investigar a proporção de perda de chamadas entre os planos tarifários A, B e C.

## Principais Resultados de Negócio
- **Mapeamento de Ineficiência:** Com os filtros aplicados, **473 operadores** (cerca de 43,3% da base) foram identificados operando de forma ineficiente em pelo menos um dos critérios vitais.
- **Falha Crítica de Priorização (H1):** O teste de Mann-Whitney U comprovou uma inversão de prioridades no atendimento: ligações de colegas (internas) são atendidas em média em 22,8s, enquanto clientes reais (externas) esperam quase 4 vezes mais na fila (96s).
- **Risco Iminente de Churn (H2):** O teste de Kruskal-Wallis revelou que as contas do Plano C enfrentam a pior degradação de serviço, apresentando uma taxa média de perda de 1,89%, necessitando de intervenção comercial urgente.
- **Entrega Operacional:** Geração de bases consolidadas (`base_chamadas_tratada.csv` e `diagnostico_operadores.csv`) prontas para alimentar dashboards gerenciais.
