# Tendências e Impacto das Mudanças Climáticas em Uberlândia-MG: Análise Exploratória de Séries Temporais de Temperatura

## Descrição do Projeto
Este projeto faz parte da Atividade Extensionista do curso de Ciência de Dados do Centro Universitário Internacional UNINTER e tem como objetivo analisar as tendências e o impacto das mudanças climáticas na cidade de Uberlândia-MG, utilizando dados meteorológicos coletados do Instituto Nacional de Meteorologia (INMET). A análise se concentra principalmente nas séries temporais de temperatura, buscando identificar padrões, tendências e variações ao longo do tempo.

## Metodologia

O projeto foi dividido nas seguintes etapas:

1.  **Coleta de Dados:**
    *   Dados meteorológicos da estação automática de Uberlândia-MG foram obtidos do INMET;
    *   As variáveis coletadas incluem: precipitação total, pressão atmosférica, temperaturas (máxima, média e mínima), umidade do ar e velocidade do vento;
    *   O período analisado compreende dados de 01/01/2005 a 31/12/2024.

2.  **Processamento de Dados:**
    *   **Limpeza:** Remoção de colunas irrelevantes e renomeação das colunas para melhor entendimento;
    *   **Transformação:** Conversão dos tipos de dados (datas para datetime, valores numéricos para float) e tratamento de separadores decimais;
    *   **Preenchimento de Lacunas:** Utilização do método de interpolação polinomial para preencher valores faltantes, garantindo a integridade da série temporal;
    *   **Criação de Variáveis:** Cálculo da amplitude diária de temperatura (diferença entre temperatura máxima e mínima).

3.  **Análise Exploratória de Dados (AED):**
    *   **Correlação:** Análise da correlação entre as variáveis meteorológicas através de um mapa de calor;
    *   **Amplitude de Temperatura Anual:** Visualização da variação da amplitude de temperatura ao longo dos anos;
    *   **Sazonalidade:** Análise do comportamento da temperatura média ao longo dos meses do ano;
    *   **Tendência da Temperatura:** Avaliação da temperatura média ao longo dos anos, comparando com dados da NASA;
    *    **Análise da Precipitação:** Visualização da precipitação ao longo dos anos e meses;

4.  **Análise e Previsão:**
    *   Implementação de modelos de previsão de temperatura máxima usando a biblioteca `Prophet`;
    *   Criação de dois modelos: um sem regressores e outro com regressores (pressão atmosférica e umidade relativa do ar);
    *   Divisão dos dados em conjuntos de treino e teste (80/20);
    *   Visualização das previsões com intervalos de incerteza, bem como das componentes da previsão (tendência e sazonalidade).

5.  **Avaliação dos Modelos:**
    *   Cálculo do erro da porcentagem média absoluta (MAPE) e da raiz do erro médio ao quadrado (RMSE) para avaliar a precisão dos modelos.

## Bibliotecas Utilizadas

*   `matplotlib` (versão utilizada: 3.10.0)
*   `numpy` (versão utilizada: 1.26.4)
*   `pandas` (versão utilizada: 2.2.2)
*   `prophet` (versão utilizada: 1.1.6)
*   `seaborn` (versão utilizada: 0.13.2)
*   `scikit-learn` (versão utilizada: 1.6.1)

## Resultados

*   O projeto demonstra as tendências de aumento da temperatura média em Uberlândia ao longo dos anos, além de mostrar como a tendência das temperaturas máximas vêm aumentando e das temperaturas mínimas, diminuindo, o que resulta em um aumento na amplitude da temperatura anual;
*   O modelo de previsão de temperatura máxima com regressores (pressão atmosférica e umidade relativa do ar) apresentou um melhor ajuste dos dados e menor erro na previsão, comparado ao modelo sem regressores;
*   O projeto visualizou a tendência de aumento das temperaturas médias, o aumento das amplitudes térmicas anuais e a sazonalidade das temperaturas.

## Como executar o projeto

1.  Certifique-se de ter o Google Colab aberto

2.  Instale a biblioteca Prophet usando o comando: `!pip install prophet`

3.  Faça o upload dos arquivos CSV com os dados meteorológicos da estação de Uberlândia (`dados_A507_D_2005-01-01_2024-12-31.csv`) e da NASA (`NASA_data_mean_temperatures.txt`) para o seu Google Drive. Você pode encontrar os arquivos nesse repositório, no diretório "data" ou <a href="https://github.com/paula-belr/series-temporais-temperatura/tree/main/data" target="_blank">clicando aqui</a>

4.  Altere o caminho do arquivo CSV no código para refletir o local onde você salvou o arquivo, dentro das células de código que carregam os dados: 

        df_auto = pd.read_csv('/content/drive/MyDrive/ColabNotebooks/dados-atividade-extensionista/estacoes-auto-uberlandia-a507-01-01-2005-31-12-2024/dados_A507_D_2005-01-01_2024-12-31 (1).csv', sep = ';', skiprows = 10)


        df_n = pd.read_csv('/content/drive/MyDrive/ColabNotebooks/dados-atividade-extensionista/NASA_mean_temperature/NASA_data_mean_temperatures.txt', skiprows = 5, names = ['Year', 'No_Smoothing', 'Lowess(5)'], sep = '\s+')
        

5.  Execute as células do notebook para reproduzir a análise e visualizar os resultados.

## Próximos passos

*   Explorar diferentes métodos de imputação de dados faltantes;
*   Incorporar outros regressores no modelo para verificar suas influências.
