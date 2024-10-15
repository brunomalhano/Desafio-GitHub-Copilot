### 1. **Jupyter Notebook Extension for VS Code (Windows)**

A extensão de Jupyter Notebook permite que você use notebooks interativamente dentro do VS Code.

#### Passos:

1. **Instalar o Visual Studio Code**:
   - Se ainda não tiver o VS Code instalado, baixe e instale-o a partir do site oficial: [VS Code](https://code.visualstudio.com/).

2. **Instalar a extensão Jupyter**:
   - Abra o VS Code.
   - No lado esquerdo da janela, clique no ícone de extensões (ícone de quadrado com um lado faltando).
   - Na barra de pesquisa, digite "Jupyter" e selecione a extensão "Jupyter" da Microsoft.
   - Clique em "Instalar" para adicionar a extensão.

3. **Instalar o Python**:
   - Caso ainda não tenha o Python instalado no sistema:
     - Baixe o Python do site oficial: [Python.org](https://www.python.org/downloads/windows/).
     - Certifique-se de selecionar a opção "Add Python to PATH" ao instalar.
   - Se já tiver o Python instalado, certifique-se de que o `python` está corretamente configurado no `PATH`.

4. **Criar e abrir um Jupyter Notebook**:
   - No VS Code, clique no menu `File > New File`, e salve o arquivo com a extensão `.ipynb`.
   - O VS Code automaticamente abrirá a interface do notebook Jupyter.

5. **Executar células de código**:
   - Escreva o código nas células e clique no ícone de "Play" para executar.
   - O kernel de Python será ativado para executar o código.

---

### 2. **Instalar PySpark Libs (Windows)**

Para configurar o PySpark no Windows, você precisa instalar algumas dependências, incluindo Python e Java.

#### Passos:

1. **Instalar o PySpark via pip**:
   - No terminal do VS Code ou no **Prompt de Comando**, execute o seguinte comando para instalar o PySpark:
     ```bash
     pip install pyspark
     ```

2. **Verificar a instalação**:
   - Para garantir que o PySpark foi instalado corretamente, abra o terminal Python no VS Code ou no Prompt de Comando e execute o seguinte:
     ```python
     import pyspark
     print(pyspark.__version__)
     ```
   - Isso retornará a versão do PySpark instalada.

3. **Instalar o Hadoop e configurar o WinUtils (necessário no Windows)**:
   - O Hadoop requer o `WinUtils.exe` para funcionar corretamente no Windows.
   - Faça o download do `winutils.exe` para a versão do Hadoop que você está usando:
     - [WinUtils Download](https://github.com/steveloughran/winutils)
   - Extraia o `winutils.exe` para um diretório, como `C:\hadoop\bin`.
   - Adicione o caminho do diretório do `winutils` à variável de ambiente `PATH`:
     1. No Windows, abra o **Painel de Controle** → **Sistema** → **Configurações avançadas do sistema**.
     2. Clique em **Variáveis de Ambiente** e, em **Variáveis de sistema**, edite a variável `PATH`.
     3. Adicione o caminho do diretório onde você colocou o `winutils.exe`, por exemplo: `C:\hadoop\bin`.

4. **Executar PySpark localmente**:
   - Você pode iniciar uma sessão PySpark em Python com o seguinte código:
     ```python
     from pyspark.sql import SparkSession

     spark = SparkSession.builder \
         .appName("MyApp") \
         .getOrCreate()

     df = spark.read.csv("myfile.csv", header=True, inferSchema=True)
     df.show()
     ```

---

### 3. **Instalar Java localmente (Windows)**

O Apache Spark requer Java (JDK), e você precisa configurá-lo corretamente no sistema Windows.

#### Passos:

1. **Baixar o Java (JDK)**:
   - Baixe o Java Development Kit (JDK) mais recente da [Oracle](https://www.oracle.com/java/technologies/javase-downloads.html) ou do [OpenJDK](https://jdk.java.net/).

2. **Instalar o JDK**:
   - Execute o instalador baixado e siga as instruções na tela.
   - Durante a instalação, o caminho do Java será automaticamente adicionado ao `PATH`, mas certifique-se de que a opção "Set JAVA_HOME" está selecionada.

3. **Verificar a instalação**:
   - Para garantir que o Java foi instalado corretamente, abra o **Prompt de Comando** e execute:
     ```bash
     java -version
     ```
   - Isso retornará a versão instalada do Java.

4. **Configurar a variável de ambiente JAVA_HOME (se necessário)**:
   - Caso o comando `java -version` não funcione, siga estes passos para configurar o `JAVA_HOME` manualmente:
     1. Abra **Painel de Controle** → **Sistema** → **Configurações avançadas do sistema**.
     2. Clique em **Variáveis de Ambiente**.
     3. Em **Variáveis de sistema**, clique em **Novo**.
     4. Adicione uma nova variável chamada `JAVA_HOME` e defina o valor para o diretório de instalação do JDK, por exemplo: `C:\Program Files\Java\jdk-17`.
     5. Em seguida, edite a variável `PATH` e adicione `;%JAVA_HOME%\bin` ao final.

5. **Testar o Java com PySpark**:
   - Teste a integração do Java com o PySpark criando uma sessão Spark:
     ```python
     from pyspark.sql import SparkSession

     spark = SparkSession.builder \
         .appName("TestSpark") \
         .getOrCreate()

     print(spark.version)
     ```

Com esses passos, você estará com o **Jupyter Notebook**, **PySpark** e o **Java** corretamente configurados no sistema **Windows**.
