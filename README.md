
# :crystal_ball: Pythonisa
[![Python](https://img.shields.io/static/v1?label=Python&message=3.8&colorA=purple&color=black&logo=Python&logoColor=white)](https://www.python.org/) 

## :book: Overview 
Pythonisa é um código que encapsula funções da biblioteca [Pulp](https://pypi.org/project/PuLP/) para resolução de problema de Programação Linear que busca maximizar lucros de uma panificadora com base nos ingredientes disponíveis no estoque.

> Curiosidade: Pithonisa, do latin *pythonīssa,ae* é a denominação utilizada na antiguidade para referir-se às mulheres que supostamente tinham o dom de prever o futuro. Também conhecida como profetisas.

<center>
<img src="https://st.depositphotos.com/1394326/1304/i/600/depositphotos_13046621-stock-photo-fortuneteller-with-crystal-ball.jpg"  width="150" height="170">
</center>

<!-- 
### Sumário
* [Funcionamento básico](#hammer-Funcionamento_básico)
    * [Métodos disponíveis](#Métodos_disponíveis)
* [Executando o código](#balloon-Executando_o_código) -->


## :hammer: Funcionamento básico
Pythonisa faz a leitura de dados de uma planilha online no serviço Google Sheets com dados baseados na receita de produção de alguns tipos de pães de uma panificadora e monta e determina a solução, quando possível.
Para isso, é necessário ter um arquivo de credenciais que dão acesso somente leitura à este arquivo. Você pode ver como gerar esse arquivo [aqui](https://developers.google.com/sheets/api)


##### Métodos disponíveis

*  **dataframeFromSheet**: Este método retorna um dataframe construído a partir da leitura de uma planilha *gsheets*.
    
    ```Python
    def dataframeFromSheet(source,
                        credentialsFilename, 
                        worksheet):
    ```
    onde 
    
    source: Endereço URL da planilha online
    credentialsFilename: Caminho do arquivo de credenciais para interação com API do Google Sheets
    worksheet: Nome da planilha


*  **mountLP(title)** 
Este método constroi o problema de PL a partir de um dataframe construído com o método dataframeFromSheet
    
    ```Python
    def mountLP(title=f"Problem_{datetime.now()}"):
    ```
    onde 
    
    title (opcional): Título dado ao objeto referente ao problema de LP.


*  **optimize()**
    Este método executa o *solver* para um problema de PL montado com o método mountLP().
    
    ```Python
    def optimize():
    ```
    
*  **showLP()**: Este método exibe o problema de PL anteriormente montado com o método mountLP().
    
    ```Python
    def optimize():
    ```

*   **getMinValuesResource()**
    **Descrição:** Determina valores mínimos de estoque de forma que a demanda seja satisfeita.
    
    ```Python
    def getMinValuesResource():
    ```

 ## :balloon: Executando o código

O trecho a seguir demonstra a execução do Pythonisa.

```Python
    myProb = BakeryProblem(From='gsheet', 
                    SheetUrl='https://docs.google.com/spreadsheets/d/1hwY2ab3CDSFSSYIu1Xnj-4vbM3iQM240EsfiFAG50EM',
                    Credentials='credentials.json')
    
    myProb.mountLP()
    myProb.showLP()
    myProb.optimize()
```