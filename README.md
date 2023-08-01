# Projeto de Engenharia de Dados (ETL) - Coin Market Cap

Este projeto foi elaborado para demonstrar uma gama de tarefas típicas em engenharia de dados, que vão desde a ingestão de dados a partir de uma API até a estruturação de um banco de dados, criação de um data lake, processamento de dados e a implementação de um ambiente de data warehousing.

##Arquitetura:

![image](https://github.com/victorthecreative/ETL---Coin-Market-Cap/assets/50841013/429a4e0e-b3ba-4a60-8519-b5d99183623f)

## Ingestão e Validação de Dados

- Foi feita a ingestão de dados usando Python para consumir informações de uma API específica.
- A validação das informações recebidas da API foi realizada.

## Organização e Armazenamento de Dados

- A informação obtida da API foi estruturada em um formato JSON, que foi posteriormente carregado em uma tabela em um banco de dados RDS na AWS.
- Um Data Lake foi implementado utilizando o serviço S3 da AWS.
- O AWS Data Migration Service (DMS) foi usado para facilitar a ingestão de dados no Data Lake.

## Processamento de Dados

- Os dados foram processados utilizando o Spark em conjunto com o Amazon EMR.
- Tabelas Delta foram criadas nas camadas "processed" e "curated".

## Disponibilização de Dados

- Crawlers foram configurados para disponibilizar as tabelas para consultas no AWS Athena.
- Workgroups foram implementados no Athena para gerenciar o acesso e os recursos.
- Foram discutidos casos de uso do Athena e como esse serviço pode ser usado para consultas ad-hoc e análises interativas.

## Implementação de Data Warehousing

- O deploy do serviço Amazon Redshift foi realizado para atuar como o data warehouse.
- Uma aplicação Spark foi implantada com o Amazon EMR, a qual escreve diretamente no Redshift, permitindo a análise de dados de grande volume.

## Infraestrutura como código

- O Terraform foi usado para provisionar os recursos AWS utilizados (RDS, DMS, Crawlers, Redshift), proporcionando uma abordagem de Infraestrutura como Código (IaC), o que aumenta a reprodutibilidade e a manutenção do projeto.

Para obter mais informações sobre este projeto de engenharia de dados, sinta-se à vontade para entrar em contato ou consultar o código-fonte para obter detalhes completos da implementação.

### Para rodar a aplicação de ingestão faça:

1. Provisione o RDS PostgreSQL na AWS conforme abordado em aula.
2. Crie um banco de dados, por exemplo: coins
3. Configure o arquivo model.py com o nome da tabela a ser criada, exemplo: tb_coins.
4. Edite variável `db_string` com o endpoint do RDS na AWS.
5. Altere o arquivo app.py inserindo a chave da api como argumento da função get_data (key)
6. Execute a aplicação para consumo da API e persistência no banco de dados.
