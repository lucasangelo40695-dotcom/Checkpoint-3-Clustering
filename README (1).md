# Checkpoint 03 - Clustering e Segmentação de Clientes

**Disciplina:** Modelagem Linear para Aprendizado de Máquina - FIAP
**Turma:** 1CCPJ

**Integrantes:**
- Gustavo Guedes Pereira - RM 569779
- Lucas Angelo - RM 569530
- Gustavo de Souza - RM 570746
- Arthur Tae - RM 570647
- Gabriel Rodrigues - RM 569322

## Objetivo
Aplicar K-Means para identificar perfis de compra em clientes de um e-commerce, justificando k com Elbow e Silhouette Score, interpretando os grupos e propondo ações de relacionamento.

## Base de dados
120 clientes fictícios (gerados com NumPy, semente 303), incorporados ao notebook como texto CSV. Não há dados reais.

| Coluna | Descrição |
| --- | --- |
| `id_cliente` | Identificador (excluído do modelo) |
| `gasto_total_12_meses` | Gasto acumulado (R$) |
| `quantidade_compras_12_meses` | Número de compras |
| `dias_desde_ultima_compra` | Recência em dias |

Sem valores ausentes e sem ids duplicados.

## Como executar
1. Python 3.9+ com: `pip install pandas numpy matplotlib scikit-learn jupyter`
2. Abrir `Checkpoint_3_MLAM_Clustering_Clientes.ipynb` (Jupyter ou Google Colab).
3. Executar todas as células na ordem. Não é necessário arquivo externo.

## Metodologia
- Variáveis: as três numéricas, padronizadas com `StandardScaler`.
- K-Means com `random_state=42` e `n_init=10`.
- Elbow (k de 1 a 8) e Silhouette Score (k de 2 a 8).

## Principais resultados
- Elbow: queda de inércia de 49,87 (k=3 para 4) e de apenas 13,73 (k=4 para 5), cotovelo em k=4.
- Silhouette: maior score em k=4 (0,5526); k=5 obteve 0,5433.
- k escolhido: **4**.

| Cluster | Clientes | Gasto médio (R$) | Compras | Dias desde a última compra | Perfil |
| --- | ---: | ---: | ---: | ---: | --- |
| 0 | 28 | 9.309,60 | 27,1 | 10,5 | Alto valor, frequente e recente |
| 1 | 30 | 6.741,40 | 6,3 | 75,6 | Alto valor, poucas compras e espaçadas |
| 2 | 32 | 2.861,70 | 22,7 | 15,0 | Frequente, ticket baixo |
| 3 | 30 | 833,30 | 4,1 | 102,4 | Baixo valor e mais distante |

As ações propostas (fidelização, reativação, aumento de ticket e teste de reativação de baixo custo) são hipóteses a validar com dados adicionais, detalhadas no notebook.

## Limitações
Base simulada e pequena, apenas três variáveis, K-Means sensível a outliers e a escolha de k, e ausência de dados como categoria, margem e satisfação.
