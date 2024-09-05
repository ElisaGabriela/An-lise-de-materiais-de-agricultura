# Análise de dados materiais de agricultura 🌱

A análise de dados exerce uma função significativa na agricultura atual, contribuindo com decisões orientadas a dados que tornam possível maiores eficiências , menores custos e maximização da produção. Por meio da análise dos preços de materiais agrícolas, como lã , madeira, borracha , se faz possível encontrar tendências, interpretar variações sazonais e prever oscilações futuras. Este projeto tramita oferecer uma análise detalhada para um conjunto de dados que contém informações sobre cada um dos materiais, com vistas a encontrar insights úteis para decisões. 

## Bibliotecas utilizadas

O seguinte conjunto de bibliotecas Python é adotado neste projeto para realizar a análise de dados e gerar as visualizações informativas correspondentes.

- **Pandas:** Uma biblioteca muito poderosa para o manuseio e análise de dados. É o principal meio adotado para carregar e limpar o dataset, usando operações de análise de dados, como correlação e agregações.

- **Numpy:** Usada para operações matemáticas e desvios de arrays. É essencial para cálculos eficientes e para a criação de matrizes de dados.

- **Seaborn:** Uma biblioteca de visualização de dados construída sobre o Matplotlib que proporciona uma interface de alto nível para visualização estatística atraente e inteligente. Este projeto a utiliza para traçar gráficos de dispersão, histogramas e mapas de calor.

- **Matplotlib:** A biblioteca primária para visualização de dados em Python, que oferece chips de trabalho para traçar gráficos e ajustar visualmente gráficos. É prudentemente utilizada neste projeto junto ao Seaborn para gráficos mais complexos e ajustáveis.

## Importação do dataframe

O conjunto de dados utilizado neste projeto foi retirado do **Kaggle**, especificamente da página ["Agricultural Raw Material Prices 1990-2020"](https://www.kaggle.com/datasets/kianwee/agricultural-raw-material-prices-19902020/data).
 Ele contém informações detalhadas sobre os preços de diversos materiais agrícolas ao longo de um período de 30 anos (de 1990 a 2020). Os dados abrangem materiais como lã, madeira, borracha e algodão, entre outros.

O dataframe foi processado a partir desse conjunto de dados, que inclui preços mensais de várias matérias-primas, permitindo a análise de tendências de preços, correlações entre diferentes materiais e flutuações sazonais. As colunas principais incluem:

Month: O mês correspondente ao preço registrado.
Material Prices: Colunas para cada material, como "Cotton Price", "Fine Wool Price", "Rubber Price", entre outros, indicando o preço desses materiais em cada mês.
Esses dados são essenciais para entender as dinâmicas de preços no setor agrícola e como diferentes fatores afetam os custos dos materiais ao longo do tempo.

## Tratamento de dados
No processo de tratamento de dados para este projeto, foram realizadas várias etapas importantes para garantir que o dataframe estivesse limpo e pronto para análise. Abaixo estão os principais passos seguidos:

- **Substituição de Caracteres:** Foram removidos caracteres indesejados, como o símbolo de porcentagem (%), vírgulas (,), e traços (-), que poderiam interferir na conversão de dados numéricos. Exemplo: '12.5%' foi transformado em '12.5' para permitir a conversão para tipo numérico.
- **Substituição de Valores Vazios por Nulo:** Onde havia valores vazios no dataset, esses foram substituídos por valores nulos (NaN). Isso permite um melhor tratamento e limpeza dos dados, já que valores nulos podem ser facilmente identificados e removidos em etapas posteriores.
- **Remoção de Valores Vazios:** Após a substituição dos valores vazios por NaN, as linhas com dados ausentes foram removidas do dataset. Essa etapa é crucial para evitar erros ou distorções nas análises, especialmente em cálculos estatísticos.
- **Conversão de Tipos:** As colunas com dados numéricos foram convertidas para o tipo float, permitindo operações matemáticas e análises de correlação. Antes da conversão, os caracteres de texto e símbolos que interferiam no formato numérico foram removidos.
- **Tratamento das Datas:** A coluna de datas foi tratada para transformar os valores de strings em um formato de data (datetime). Isso facilita o uso de funções baseadas em tempo e a ordenação dos dados ao longo do eixo temporal. Exemplo: 'Jan-20' foi convertido para 2020-01-01, no formato datetime.
- **Definindo as Datas como Índice:** Após a conversão da coluna de datas, ela foi definida como o índice do dataframe. Isso facilita a visualização e manipulação dos dados ao longo do tempo, além de permitir gráficos que mostrem a evolução dos preços por mês de forma clara e ordenada.
Essas etapas de tratamento de dados garantem que o conjunto de dados esteja bem formatado e adequado para as análises de preços e correlações entre os materiais agrícolas.

## Análises realizadas
Neste projeto, foram realizadas diversas análises para entender melhor o comportamento dos preços das matérias-primas agrícolas. Abaixo estão os principais métodos aplicados:

- **Matriz de Correlação:** Foi construída uma matriz de correlação para identificar a relação entre os preços das diferentes matérias-primas. A matriz de correlação é uma tabela que mostra o coeficiente de correlação entre pares de variáveis. Esse coeficiente varia de -1 a 1, onde: '1' indica uma correlação positiva perfeita (quando uma variável aumenta, a outra também aumenta de forma proporcional). '-1' indica uma correlação negativa perfeita (quando uma variável aumenta, a outra diminui de forma proporcional). '0' indica que não há correlação entre as variáveis. A maior correlação encontrada foi entre os preços de Fine Wool e Coarse Wool, sugerindo que os dois tipos de lã apresentam um comportamento de mercado muito semelhante. Isso ocorre provavelmente porque ambos os materiais são derivados da lã de ovelhas, sendo influenciados por fatores similares, como condições climáticas, demanda global e produção em áreas geográficas semelhantes.
  ![Matriz de correlação dos preços](https://i.imgur.com/Tyekoto.jpeg)
- **Gráfico de Regressão Linear:** Para examinar melhor a relação entre Fine Wool e Coarse Wool, foi gerado um gráfico de regressão linear, que mostrou uma linha reta indicando uma forte correlação entre os dois preços. Isso confirma que os movimentos de preços dessas duas matérias-primas estão altamente relacionados, reforçando a ideia de que os mesmos fatores de mercado impactam ambas de forma semelhante.
  ![Regressão linear](https://i.imgur.com/pRT34Vu.jpeg)
  ![Variação dos preços](https://i.imgur.com/Ms53f7M.jpeg)
- **Matriz de Correlação para Variação Percentual dos Preços:** Também foi feita uma análise da matriz de correlação para a variação percentual dos preços. Curiosamente, não foi encontrada nenhuma correlação significativa entre as variações percentuais dos preços das matérias-primas. Isso indica que, apesar de algumas matérias-primas apresentarem correlação em seus preços absolutos, as flutuações percentuais nos preços ao longo do tempo parecem ser independentes.
 ![Matriz de correlação da variação dos preços](https://i.imgur.com/AlyhDGm.jpeg)
- **Análise da Variação dos Preços ao Longo do Tempo:** Foi criada uma série de gráficos de linha para visualizar a variação dos preços de todas as matérias-primas ao longo do tempo. Posteriormente, foram analisadas apenas as cinco matérias-primas com os maiores preços médios ao longo do período estudado. Além disso, foram destacados os menores e maiores preços de cada matéria-prima ao longo do tempo, permitindo uma visão clara dos pontos mais críticos do mercado.
![Variação dos preços ao longo do tempo](https://i.imgur.com/BW0wpZI.jpeg)
![Variação dos preços ao longo do tempo - top 5](https://i.imgur.com/vyuyh9d.jpeg)
![Variação dos preços ao longo do tempo - maior preço](https://i.imgur.com/j6km5cV.jpeg)
![Variação dos preços ao longo do tempo - menor preço](https://i.imgur.com/Tx2a7O6.jpeg)
- **Análise de Histogramas:** Também foi gerada uma análise em histogramas da variação percentual dos preços das matérias-primas. Esses histogramas ajudam a avaliar a volatilidade e o risco associado ao mercado de cada matéria-prima. A distribuição das variações percentuais nos preços permite entender quais matérias-primas são mais estáveis e quais apresentam maiores flutuações, o que pode influenciar decisões de investimento e planejamento estratégico no setor agrícola.
![Variação dos percentuais da materia prima](https://i.imgur.com/vr1Q6ie.jpeg)
Essas análises proporcionam uma visão abrangente do comportamento dos preços das matérias-primas agrícolas, ajudando a identificar padrões, riscos e oportunidades no mercado.
