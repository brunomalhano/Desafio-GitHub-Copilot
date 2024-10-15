# Desafio-GritHub-Copilot

### Desafios:

**1. Ler e transformar os dados de corridas de táxi:**
- Usando PySpark, leia o arquivo CSV `yellow_tripdata_example.csv`.
- Realize as seguintes transformações:
  - Converta a coluna `pickup_datetime` para o formato de data e hora apropriado.
  - Calcule uma nova coluna `trip_duration` (duração da viagem) em minutos, com base nas colunas de `pickup_datetime` e `dropoff_datetime`.

**2. Filtragem e agregação de dados:**
- Crie um pipeline de PySpark que:
  - Filtre corridas com mais de 2 passageiros e distâncias de viagem maiores que 10 milhas.
  - Calcule a média e a mediana do valor da corrida (`total_amount`) para esse conjunto filtrado.
  
**3. Validação e limpeza de dados:**
- Verifique se os campos numéricos (`passenger_count`, `trip_distance`, `total_amount`) contêm valores negativos ou nulos.
- Remova registros que apresentem esses valores inválidos e registre quantos registros foram removidos.

**4. Testes unitários:**
- Crie testes unitários utilizando `pytest` para validar as transformações realizadas nos dados:
  - Teste a função que calcula a duração da viagem.
  - Teste se a filtragem de dados está sendo feita corretamente com base nas condições definidas.

**5. Detecção de outliers:**
- Usando PySpark, identifique corridas que tenham valores muito acima ou abaixo da média para as colunas `trip_distance` e `total_amount`.
- Crie uma função para rotular esses registros como "outliers" e salve-os em um novo DataFrame.

**6. Análise temporal:**
- Agrupe os dados por hora do dia (com base na coluna `pickup_datetime`) e calcule:
  - O número de corridas por hora.
  - A média de passageiros por corrida por hora.
- Visualize os resultados usando uma biblioteca de visualização como Matplotlib ou Seaborn.

**7. Segurança de dados:**
- Implemente uma função de hash para anonimizar as colunas `VendorID` e `payment_type`, preservando a privacidade dos dados.
- Valide a função verificando se os IDs originais não podem ser facilmente recuperados a partir dos hashes.

**8. Geração de documentação automática:**
- Utilize GitHub Copilot para gerar a documentação para cada função do código.
- Revise e ajuste a documentação gerada para garantir que está clara e correta.

**9. Deploy da aplicação no Azure:**
- Crie um template Terraform que provisione a infraestrutura necessária no Azure, incluindo:
  - Um cluster Databricks para o processamento dos dados.
  - Um banco de dados SQL para armazenar os resultados de agregações e análises.

Esses desafios permitem que os participantes usem GitHub Copilot para gerar soluções que envolvem manipulação de dados em PySpark, testes, segurança, documentação e infraestrutura no Azure.
