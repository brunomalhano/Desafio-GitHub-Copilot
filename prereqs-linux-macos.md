### 1. **Jupyter Notebook Extension for VS Code**

A extensão de Jupyter Notebook permite que você use notebooks interativamente dentro do VS Code.

#### Passos:

1. **Instalar o Visual Studio Code**:
   - Se ainda não tiver o VS Code instalado, baixe e instale-o a partir do site oficial: [VS Code](https://code.visualstudio.com/).

2. **Instalar a extensão Jupyter**:
   - Abra o VS Code.
   - No lado esquerdo da janela, clique no ícone de extensões (ícone de quadrado com um lado faltando).
   - Na barra de pesquisa, digite "Jupyter" e selecione a extensão "Jupyter" da Microsoft.
   - Clique em "Instalar" para adicionar a extensão.

3. **Verificar dependências do Python**:
   - Se o Python não estiver configurado no VS Code, você será solicitado a instalar o Python quando abrir um notebook Jupyter.
   - Caso não tenha o Python instalado em seu sistema, instale a versão mais recente a partir do [site oficial do Python](https://www.python.org/).

4. **Criar e abrir um Jupyter Notebook**:
   - No VS Code, abra o painel "Explorer" e clique com o botão direito em uma pasta ou no espaço em branco.
   - Selecione "New File" e nomeie o arquivo com a extensão `.ipynb`.
   - O VS Code abrirá automaticamente o notebook com a interface interativa.

5. **Executar células de código**:
   - Escreva o código dentro das células e clique no ícone de "Play" para executar a célula.
   - O VS Code utilizará o kernel de Python para executar o código, similar ao funcionamento do Jupyter Notebook no navegador.

---

### 2. **Instalar PySpark Libs**

O PySpark é a interface Python para o Apache Spark, e é necessário configurar algumas dependências antes de poder utilizá-lo.

#### Passos:

1. **Instalar o PySpark via pip**:
   - No terminal do VS Code ou diretamente no terminal do sistema, execute o seguinte comando para instalar o PySpark:
     ```bash
     pip install pyspark
     ```

2. **Verificar a instalação**:
   - Abra um terminal Python e execute o seguinte código para verificar se o PySpark foi instalado corretamente:
     ```python
     import pyspark
     print(pyspark.__version__)
     ```
   - Isso exibirá a versão do PySpark instalada, confirmando que tudo está correto.

3. **Instalar dependências adicionais (opcional)**:
   - Para trabalhar com dados grandes e melhorar a performance de I/O, você pode instalar bibliotecas adicionais, como `hadoop-aws`, para trabalhar com arquivos armazenados no Amazon S3:
     ```bash
     pip install hadoop-aws
     ```

4. **Executar PySpark localmente**:
   - Você pode criar uma sessão do PySpark em seu código Python com o seguinte código:
     ```python
     from pyspark.sql import SparkSession

     spark = SparkSession.builder \
         .appName("MyApp") \
         .getOrCreate()

     df = spark.read.csv("myfile.csv", header=True, inferSchema=True)
     df.show()
     ```

5. **Testar a configuração**:
   - Execute o código acima em um notebook Jupyter no VS Code para garantir que o PySpark foi instalado corretamente e está funcionando.

---

### 3. **Instalar Java localmente**

O Apache Spark requer uma instalação local do Java, pois depende do ambiente JVM (Java Virtual Machine).

#### Passos:

1. **Baixar o Java (JDK)**:
   - Acesse o site oficial do Java Development Kit (JDK) para baixar a versão mais recente:
     - [Oracle JDK](https://www.oracle.com/java/technologies/javase-downloads.html)
     - [OpenJDK (alternativa gratuita)](https://openjdk.java.net/install/)

2. **Instalar o JDK**:
   - Após baixar o instalador, siga os passos para concluir a instalação.
   - No Windows, o instalador irá automaticamente adicionar o caminho do Java à variável de ambiente `PATH`. No Linux ou macOS, você pode precisar ajustar manualmente.

3. **Verificar a instalação**:
   - Para garantir que o Java foi instalado corretamente, abra um terminal e execute:
     ```bash
     java -version
     ```
   - Isso deverá retornar a versão do Java instalada, confirmando que tudo está funcionando.

4. **Configurar variáveis de ambiente (se necessário)**:
   - Caso o comando acima não funcione, será necessário adicionar o caminho do Java à variável de ambiente `PATH`.
   - No Windows:
     1. Abra "Painel de Controle" → "Sistema e Segurança" → "Sistema" → "Configurações avançadas do sistema".
     2. Clique em "Variáveis de ambiente".
     3. Em "Variáveis de sistema", edite a variável `PATH` e adicione o caminho da instalação do Java (ex: `C:\Program Files\Java\jdk-xx\bin`).
   - No macOS/Linux:
     - Adicione a seguinte linha ao arquivo `~/.bashrc` ou `~/.zshrc`:
       ```bash
       export PATH=$PATH:/usr/lib/jvm/java-xx-openjdk/bin
       ```

5. **Configurar o JAVA_HOME**:
   - Também é necessário definir a variável `JAVA_HOME`. Adicione a linha apropriada ao seu arquivo de perfil de ambiente:
     - Windows:
       ```bash
       setx -m JAVA_HOME "C:\Program Files\Java\jdk-xx"
       ```
     - macOS/Linux:
       ```bash
       export JAVA_HOME=/usr/lib/jvm/java-xx-openjdk
       ```

6. **Testar com PySpark**:
   - Agora, o ambiente Java está pronto para ser utilizado com PySpark. Teste criando uma sessão do Spark no Python:
     ```python
     from pyspark.sql import SparkSession

     spark = SparkSession.builder.appName("TestSpark").getOrCreate()
     print(spark.version)
     ```

Seguindo esses passos, você terá o ambiente configurado com o Jupyter Notebook no VS Code, PySpark instalado, e o Java pronto para rodar o Apache Spark.
