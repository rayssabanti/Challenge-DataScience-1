## :dna: Semana 1
* :pushpin: **Semana 1** - limpeza dos dados trazidos de uma API
    * Analisar a variável target: Churn :heavy_check_mark:
    * Visualizar a distribuição da variável target: Churn :heavy_check_mark:
    * Criar visualizações relevantes em relação ao Churn :heavy_check_mark:
    * Analisar a correlação das variáveis :heavy_check_mark:
    * Testar diferentes tipos de gráficos  :heavy_check_mark:
### :bookmark: Importação das bibliotecas
* Pandas
* Seaborn
* MatplotLib.pyplot

### :bookmark: Importação dos dados 
Utilizado os dados limpos na primeira semana 
*(Salvo na pasta: Dados\DadosTelco.csv)*
### :wastebasket:	Análise Exploratória: Churn 
Toda a análise a seguir foi focada na variável cancelouPlano aka Churn, com o foco em entender sua distribuição nas variáveis correlacionadas, e como podemos entender o motivo do cancelamento.
#### A Variável Churn 
Comecei entendendo quantos dos nossos clientes cancelaram o plano.
![image](https://user-images.githubusercontent.com/61653788/172034100-111edee4-7eb0-4852-9fd3-aa1760c9dbe5.png)
O número de cancelamentos é visualmente pequeno, sendo de 25%, porém ainda é um número alto levando em conta as correlações que vem a seguir.
#### Correlações com as outras variáveis 
Com o heatmap conseguimos verificar as correlações entre variáveis numéricas e ter uma visão ampliada da sinergia dos dados. 
Porémm, apenas algumas colunas são numéricas, nesse caso realizamos o encode numérico em todas as colunas:


