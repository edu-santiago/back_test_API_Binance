# Back_test_API_Binance

Read this in other languages: [English](https://github.com/Kalienel/back_test_API_Binance/blob/main/README.en.md)

Essa ferramenta foi desenvolvida para calcular possíveis retornos em qualquer par de moedas da Binance com estratégias utilizando indicadores de análise técnica do módulo [TA](https://technical-analysis-library-in-python.readthedocs.io/en/latest/)  do Python

### Requirements
- Pandas
- Numpy
- Matplotlib
- Seaborn
- binance-connector
- ta

### Funções de preparação

A função market_data puxa os dados especificados diretamente da API da Binance e retorna um dataframe tratado com as informações dos candlesticks
A load_market pega os dados da market_data e adiciona os indicadores que devem ser visualizados, já vindo EMA 9, EMA 26 e RSI 7 por padrão, buscando dados a nível diário
plot_market busca os dados da load_market e plota as informações, ela também pode receber uma lista de momentos de compra e venda, output da função back_test


### Função Back_test

A função back_test recebe do load_market o dataframe com preços e indicadores e o dinheiro inicial. O seu np.where é onde é decidido se é um momento de compra e venda da moeda, já vindo com uma estratégia básica de EMA crossover imbutida + RSI abaixo de 80. Retornando um dataframe com o lucro, o lucro percentual e o valor final acumulado.

Seu funcionamento é baseado na iteração por período de tempo, aplicando a estratégia tomando cada ponto de dado como um momento inicial e identificando o lucro se o investimento tivesse sido feito em cada cada disponível.

Por fim ela retorna um CSV que pode ser analisado como o usuário desejar
