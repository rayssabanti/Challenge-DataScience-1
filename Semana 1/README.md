## :dna: Semana 1
* :pushpin: **Semana 1** - limpeza dos dados trazidos de uma API
    * Entender quais informações o conjunto de dados possui :heavy_check_mark:
    * Analisar quais os tipos de dados :heavy_check_mark:
    * Verificar quais são as inconsistências nos dados :heavy_check_mark:
    * Corrigir as inconsistências nos dados :heavy_check_mark:
    * Traduzir as colunas 
    * Criar coluna de contas diárias :heavy_check_mark:
### :bookmark: Importação das bibliotecas
* Pandas
### :bookmark: Importação dos dados 
Os dados foram disponibilizados em json, pois foram trazidos diretamente da API.
*(Arquivo original salvo na pasta: Dados\Telco-Customer-Churn.json)*
### :wastebasket:	Limpeza dos Dados
#### :card_file_box:	 Extração das colunas do json 
Quando acabamos de importar os dados - a maioria das colunas (4) ainda tem dados em formato JSON para serem extraídos.
<img src="https://user-images.githubusercontent.com/61653788/167664496-b1627402-2704-4942-a23a-b018334b18c1.png" width="800">
 Utilizando o **pd.json_normalize** extrai os dados das 4 colunas e concatenei com o dataset:
<img src="https://user-images.githubusercontent.com/61653788/167664992-fad8c395-af03-4327-9d87-8622eac3a776.png" width="800">
 
 No final temos 21 colunas no dataset.
#### :card_file_box:	 Padronizando e traduzindo o nome das colunas 
Realizei a tradução e padronização do nome das colunas (primeira palavra minuscula, segunda palavra com a primeira letra maiúscula).
<img src="https://user-images.githubusercontent.com/61653788/167696792-521d6247-261a-49c2-9798-140d40757b22.png" width="440">
#### :mag: Buscando registro nullos
Verificamos se existia algum registro null para limpar, porém não foi apontado.<br>
<img src="https://user-images.githubusercontent.com/61653788/167697572-c13ce07c-0024-4433-9877-477530734e32.png" width="440"><br>
#### :round_pushpin:	 Mudando o tipo das colunas
Foi verificado que as colunas cidadaoIdoso, mesesContrato, totalServicosMensalmente e totalGasto devem ser numéricas e apenas o totalGasto estava fora disso. 
E com isso, descobri que a coluna tinha campos com " " e teriamos que verificar e limpar novamente as colunas com esse padrão.<br>
<img src="https://user-images.githubusercontent.com/61653788/167698418-cdc35cbb-d782-4c16-90f8-f5f9ae136848.png" width="300"><br>
Procurando por colunas com casos de "" e '', descobri que apenas a cancelouPlano e totalGasto tem esses registros, então realizei a limpeza conforme:<br>
<img src="https://user-images.githubusercontent.com/61653788/167699704-193f209c-d03c-49d1-ba62-429a5f802795.png" width="440"><br>
#### :round_pushpin:	 Alterando os registros da coluna cidadaoIdoso
Alterei os registros de 0 e 1 para Não e Sim, respectivamente.<br>

<img src="https://user-images.githubusercontent.com/61653788/167908855-79599fc0-112c-463a-82cb-1fd057805ffa.png" width="440"><br>
### :mag:	Análise Exploratória
Verifiquei os registros inputados em cada coluna:<br>

<img src="https://user-images.githubusercontent.com/61653788/167702535-c2395fee-c106-4997-8560-d8c9cb5df24a.png" width="840"><br>
#### :round_pushpin:	 Tipo de dados no dataset
* :round_pushpin:	 **Dados Quantitativos:**
  São números que representam contagens ou medidas (renda e anos de escolaridade,por exemplo). 
  Esses dados se dividem em discretos e contínuos:
  * **Discreto:**
    Os dados discretos são aqueles em que o número de valores possíveis são finitos ou “enumeráveis” (tal como o número de cômodos em um domicílio).
    * MesesContrato
  * **Contínuo:**
    Os dados contínuos resultam de infinitos valores possíveis em uma escala contínua (renda per capita).
    * totalServicosMensalmente 
    * totalGasto 
 * :round_pushpin:	 **Dados Qualitativos ou Categóricos:**
  Se distinguem por alguma característica não-numérica (sexo e raça, por exemplo).
  * **Nominal:**
    Utiliza dados que informam nomes, rótulos ou categorias. Os dados não são ordenados e não devem ser usados para cálculos de médias, como é o caso de raça e código do município, por exemplo.
    * ClienteID
    * cancelouPlano
    * genero 
    * cidadaoIdoso 
    * temParceiro 
    * temDependentes 
    * mesesContrato
    * assinaturaTelefonica 
    * multiplasLinhas 
    * provedorInternet 
    * segurancaOnline 
    * backupOnline 
    * protecaoDispositivo 
    * suporteTecnico 
    * streamingTV 
    * streamingFilmes 
    * tipoContrato 
    * contaOnline
    * formaPagamento  
    
#### :round_pushpin: Traduzindo os dados Qualitativos
Realizei a tradução dos registros qualitativos

<img src="https://user-images.githubusercontent.com/61653788/167909527-f2ef2a39-f365-4157-a35b-0616ef5648d1.png" width="840"><br>

#### :round_pushpin: Criar coluna de contas diárias
É necessário calcular em uma nova coluna o gasto diário por cliente na posição 18 das colunas.
<img src="https://user-images.githubusercontent.com/61653788/167713855-f4a838b9-324f-4b5c-83b8-e64f8e1885ed.png" width="740"><br>
##### :round_pushpin: Validando os valores da coluna gastoTotal
Em teoria o gasto total por cliente seria os meses de contrato x valor mensal, realizando esse cálculo encontrammos valores diferentes dos contidos na coluna gastoTotal.

<img src="https://user-images.githubusercontent.com/61653788/167714194-11e13526-c2cc-4ff8-929a-b6a3301041ff.png" width="540"><br>
<img src="https://user-images.githubusercontent.com/61653788/167714239-5888ef54-4e19-46f3-bd24-b0da67de0ea1.png" width="540"><br>
<img src="https://user-images.githubusercontent.com/61653788/167714789-d3ecfa33-2d72-42b6-b0db-4c428b9ecae8.png" width="740"><br>

#### :round_pushpin: Exportado os dados limpos para CSV
![image](https://user-images.githubusercontent.com/61653788/172026170-a8a6697a-5994-4479-96c4-8e517b01e615.png)
