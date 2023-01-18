# ETL with Airflow
Data Extract-Transform-Load pipeline with Airflow
Project made as part of the Alkemy Aceleration Program.

## Files

### universidades_grupo_E_etl.py
DAG file with the 3 sequential tasks in the ETL process.

### scripts/extract_data.py 
Callable function for extract task in DAG 'universidades_grupo_E_etl'.
   Extracts data from a Postgres DataBase contained information of universities (group E)
    and saves them locally in csv files.
It uses the queries files
query_grupo_E_interam.sql
query_grupo_E_pampa.sql

### scripts/process_data.py 
Transform data from csv files where column information comes
        in the following order:
        - index
        - university name
        - career
        - inscription date
        - name
        - gender
        - birth date
        - location or postal code
        - email
        The processed data are saved in txt files.


Requirements for final data:
- university: str minúsculas, sin espacios extras, ni guiones
- career: str minúsculas, sin espacios extras, ni guiones
- inscription_date: str %Y-%m-%d format
- first_name: str minúscula y sin espacios, ni guiones
- last_name: str minúscula y sin espacios, ni guiones
- gender: str choice(male, female)
- age: int
- postal_code: str
- location: str minúscula sin espacios extras, ni guiones
- email: str minúsculas, sin espacios extras, ni guiones

Aclaraciones: Para calcular codigo postal o locación se va a utilizar el .csv que se encuentra en el repo.La edad se debe calcular en todos los casos

### scripts/upload_file.py
Upload transformed txt files to a S3 bucket.
