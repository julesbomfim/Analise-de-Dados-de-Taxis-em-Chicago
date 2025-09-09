# Análise de Dados de Táxis em Chicago

Este repositório contém a análise de dados de corridas de táxi na cidade de Chicago, utilizando dados de novembro de 2017. O projeto foca em duas áreas principais: uma análise exploratória para identificar as empresas de táxi mais populares e os bairros de destino mais comuns, e um teste de hipótese estatística para avaliar o impacto das condições climáticas na duração das viagens.

## 📊 Arquivos de Dados

O projeto utiliza três conjuntos de dados distintos em formato `.csv`:

1.  **/datasets/project_sql_result_01.csv**:
    -   `company_name`: Nome da empresa de táxi.
    -   `trips_amount`: Número total de corridas por empresa nos dias 15 e 16 de novembro de 2017.

2.  **/datasets/project_sql_result_04.csv**:
    -   `dropoff_location_name`: Nome do bairro de destino.
    -   `average_trips`: Média de corridas que terminaram em cada bairro durante o mês de novembro de 2017.

3.  **/datasets/project_sql_result_07.csv**:
    -   `start_ts`: Data e hora de início da corrida.
    -   `weather_conditions`: Condição do tempo ("Good" ou "Bad").
    -   `duration_seconds`: Duração da corrida em segundos para viagens do bairro Loop para o Aeroporto Internacional O'Hare.

## 🛠️ Metodologia e Etapas do Projeto

A análise foi dividida em duas etapas principais:

### Passo 4: Análise Exploratória de Dados
1.  **Importação e Inspeção**: Os dados dos arquivos `01.csv` e `04.csv` foram carregados em DataFrames do Pandas e inspecionados para verificar a estrutura e os tipos de dados.
2.  **Identificação do Top 10**: Os bairros foram ordenados para identificar os 10 principais destinos com base na média de corridas.
3.  **Visualização**: Foram criados gráficos de barras para visualizar:
    -   O número de corridas das principais empresas de táxi.
    -   A média de corridas para os 10 bairros de destino mais populares.
4.  **Análise de Resultados**: Foram tiradas conclusões com base nos padrões observados nos gráficos.

### Passo 5: Teste de Hipótese
1.  **Hipótese**: Testar a afirmação: *"A duração média dos passeios do Loop para o Aeroporto Internacional O'Hare muda nos sábados chuvosos."*
2.  **Formulação**:
    -   **Hipótese Nula (H₀)**: A duração média das viagens em sábados com tempo bom é **igual** à duração média em sábados com tempo ruim.
    -   **Hipótese Alternativa (H₁)**: A duração média das viagens em sábados com tempo bom é **diferente** da duração média em sábados com tempo ruim.
3.  **Preparação dos Dados**: O arquivo `07.csv` foi carregado, a coluna de data foi convertida, e os dados foram filtrados para criar duas amostras independentes: viagens em sábados com tempo "Good" e com tempo "Bad".
4.  **Execução do Teste**: Um teste t de Student para amostras independentes foi realizado, utilizando `equal_var=False` após a verificação de que as variâncias das duas amostras eram diferentes. O nível de significância (alfa) foi definido como `0.05`.
5.  **Conclusão Estatística**: O p-valor resultante foi comparado com o alfa para rejeitar ou não a hipótese nula.

## 📈 Principais Conclusões

### Análise Exploratória
-   **Empresas de Táxi**: O mercado é dominado por um pequeno número de empresas. A "Flash Cab" é a líder de mercado com uma margem significativa sobre a segunda colocada.
-   **Bairros de Destino**: O bairro "Loop", centro comercial de Chicago, é o destino mais popular, seguido por outras áreas centrais como "River North" e "Streeterville".

### Teste de Hipótese
-   O p-valor obtido no teste foi extremamente baixo (`6.73e-12`), muito menor que o nível de significância de 0.05.
-   **Conclusão**: A hipótese nula foi rejeitada. Há evidências estatísticas robustas para afirmar que a duração média das viagens do Loop para o Aeroporto Internacional O'Hare **muda significativamente** nos sábados chuvosos.

## 💻 Tecnologias Utilizadas
-   Python 3
-   Pandas
-   Matplotlib
-   Seaborn
-   SciPy

## 🚀 Como Executar o Projeto

1.  Clone este repositório.
2.  Instale as bibliotecas necessárias:
    ```bash
    pip install pandas matplotlib seaborn scipy
    ```
3.  Certifique-se de que os arquivos `.csv` estão no diretório `/datasets/` ou ajuste os caminhos no notebook.
4.  Execute o Jupyter Notebook para visualizar a análise completa.
