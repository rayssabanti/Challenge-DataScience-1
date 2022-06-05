## :dna: Alura Challenge Data Science - 1
Esse desafio consiste em desenvolver e aplicar  habilidades de Ciência de dados como explorar, tratar e modelar os dados, focando na otimização de cada um dos modelos com a finalidade de obter o melhor resultado para a tomada de decisão. 

O desafio terá 4 semanas divididos em: 
* :pushpin: **Semana 1** - limpeza dos dados trazidos de uma API :heavy_check_mark:
* :pushpin: **Semana 2** - Explorando os dados: vendo as informações por uma outra perspectiva  :heavy_check_mark:
* :pushpin: **Semana 3 e 4** - Exterminando o futuro: Criando modelos de ML :hammer_and_wrench:	


## Semana 1
### :mag: Overview
[Mais detalhes do processo aqui](https://github.com/rayssabanti/Challenge-DataScience-1/tree/main/Semana%201)
 <br>
Realizar o entendimento inicial dos dados, quantas colunas e registros, com qual tipo de dados estamos trabalhando e se existem registros null/na. 
* **Entender quais informações o conjunto de dados possui** :heavy_check_mark:
   * Json trouxe acoplado algumas colunas - custumer, phone, internet e account ainda possuem informações acopladas, extraimos as informações para novas colunas usando o json_normalize. <br>
      ![image](https://user-images.githubusercontent.com/61653788/172026281-2ccecbec-f6ed-4e73-a72e-ba3a9ad94fd5.png)
   * E adicionamos ao dataset, tendo no final 21 colunas<br>
       <img src="https://user-images.githubusercontent.com/61653788/172026377-e1a7dd0e-aba3-4c79-892c-4fa2bcc53812.png" width="450">
* **Analisar quais os tipos de dados** :heavy_check_mark: 
    * Utilizando o Dtype, verifiquei os tipos de dados de cada coluna, e alterei aqueles que não faziam sentido.<br>
      <img src="https://user-images.githubusercontent.com/61653788/172026468-8d01c92f-2d50-4493-beeb-1e272918416e.png" width="300">
* **Verificar quais são as inconsistências nos dados** :heavy_check_mark:   
   * Realizei a busca por nulos em todas as colunas utilizando o isnull()<br>
      <img src="https://user-images.githubusercontent.com/61653788/172026483-de9f8c80-6e0f-41f5-a0b1-931bf48c8af4.png" width="300">
   * Porém, eu percebi no desafio anterior, que as colunas totalGasto e cancelouPlano, tinham campos com " " que nem o isna() ou isnul() detectaram.<br>
     <img src="https://user-images.githubusercontent.com/61653788/172026622-b0682dab-38b8-4b8d-b5dd-0e22e35bf320.png" width="450">
* **Corrigir as inconsistências nos dados** :heavy_check_mark:
   * Então com um for, realizei a correção, substituindo por 0 ou Sem Informação <br>
     <img src="https://user-images.githubusercontent.com/61653788/172026512-fe969164-b0f3-4e6e-98e4-8f27a91657a9.png" width="440">
* **Traduzir as colunas** 
   * Realizei a padronização e tradução usando o rename() <br>
     <img src="https://user-images.githubusercontent.com/61653788/172026710-f085e8f5-2dda-4ffb-b606-d6a752b48f9b.png" width="440">
   * E realizei a tradução dos dados <br>
     <img src="https://user-images.githubusercontent.com/61653788/172026749-79296447-383b-4c47-827b-3734bee415a1.png" width="450">
* **Criar coluna de contas diárias** :heavy_check_mark:
   * Criei a coluna de contas diarias com a fórmula *gastoDiario = valormensal / 30* e inseri na posição 18
     <img src="https://user-images.githubusercontent.com/61653788/172026767-1810e9a9-f8b8-437f-b90a-e94754d79fb5.png" width="440">
     <BR>
   
   
[Mais detalhes do processo aqui](https://github.com/rayssabanti/Challenge-DataScience-1/tree/main/Semana%201)
## :bookmark: Semana 2
### :mag: Overview
 [Mais detalhes do processo aqui](https://github.com/rayssabanti/Challenge-DataScience-1/tree/main/Semana%202)
 <br>
Realizar a exploração dos dados em principal foco a nova variável Churn, buscando correlações e distribuições com as outras variáveis.
* **Analisar a variável target: Churn**  :heavy_check_mark:
 * Foi verificado a distribuição da variável cancelouPlano, observamos que é uma porcentagem menor dos casos que os clientes cancelam o plano, porém ainda é necessário uma análise das correlações. <br>
   <img src="https://user-images.githubusercontent.com/61653788/172032913-f280f8ed-951f-4a00-bb8f-d691103aea1c.png" width="370">
* **Visualizar a distribuição da variável target: Churn**   :heavy_check_mark:
  * Veriiquei a relação da distribuição com as variáveis mais correlacionadas no heatmap: mesesContrato e totalServicosMensalmente <BR>
   <img src="https://user-images.githubusercontent.com/61653788/172033193-ef0eda8f-ec87-4673-a857-f158c44ed4c3.png" width="800">
    <img src="https://user-images.githubusercontent.com/61653788/172033366-d45fae70-db9c-4167-be56-34528925c7ab.png" width="800">
* **Criar visualizações relevantes em relação ao Churn**  :heavy_check_mark: <br>
   <img src="https://user-images.githubusercontent.com/61653788/172033483-b198a5fc-8b60-478e-9f28-148794733081.png" width="700">
   <img src="https://user-images.githubusercontent.com/61653788/172033501-51cf59b3-6e76-4cdd-a77e-47d85b5fa925.png" width="350">
* **Analisar a correlação das variáveis** :heavy_check_mark:
  * Utilizando após realizar o encode numérico de todas as variáveis, utilizei o .corr e o heatmap para visualizar as correlações <br>
   <img src="https://user-images.githubusercontent.com/61653788/172033616-a9c52f4e-2b47-4f98-9195-78dc26c67d85.png" width="700"> <br>
 
**Conclusão:**
- Idosos tem uma alta taxa de cancelamento
- Pessoas que não tem segurança online tem cancelado mais 
- Pessoas sem backup online tem cancelado mais 
- Pessoas que não tem suporte tem cancelado mais 
- Pessoas com contratos mensais tem mais chance de cancelar o plano e cancelam nos primeiros meses
- As pessoas que cancelam pagam mensalmente entre 70-100 reais
- Pessoas com conta eletrônica tem uma alta taxa de cancelamento

Logo, clientes novos tem mais tendência de cancelar o seu plano comparado com clientes antigos. Os clientes com menos serviços (Segurança Online, suporte e backup) tem mais chances de cancelar, provavelmente porque o plano "deixa a desejar" nesses pontos, dificultando o uso. 
As pessoas preferem o pagamento eletrônico, porém a maioria das pessoas que cancelam utilizam a conta eletrônica e tem o contato mensal. Verificamos que os clientes que pagam entre 70-100 mensalmente tem mais chances de cancelar o plano (seria interessante verificar planos de desconto pensando na permanencia dos proximos clientes). <br>
 [Mais detalhes do processo aqui](https://github.com/rayssabanti/Challenge-DataScience-1/tree/main/Semana%202) <br>
 
 ## :bookmark: Semana 3
### :mag: Overview
 [Mais detalhes do processo aqui](https://github.com/rayssabanti/Challenge-DataScience-1/tree/main/Semana%202)
 <br>

