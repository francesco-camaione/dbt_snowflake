Welcome to dbt snowflake pipelines project!

To run this project there are some things to configure:
## configure dbt using your terminal by running the followin commands inside a generic repo
1. pip install dbt-core
2. pip install dbt-snowflake

## Then setup the environment inside snowflake, after creating an account
1. execute the commands contained in the snowflake_env_setup.txt file. (I used the Sample queries on TPC-H dataset)
2. Finally execute 'dbt init' command in the terminal and insert the information available in the snowflake env setup file, for example for warehouse I named mine dbt_wh
   (Please note that the account number to insert can be found in the Profile -> copy account identifier. E.g. abcdefg.hi1234 and transform it to abcdefg-hi1234)

## Configure dbt_project.yml file
Modify the informations in the 'models object' if you want to name things differently.
In my case I created two tables: stagings table as a view and another table called marts, materialized as a table. Both in the dbt_wh warehouse.

1. Install packages by running dbt deps in the terminal


Folders are oganized so that:
- models contains SQL logic:
   - marts tables 
   - staging folder contains source datasets, staging files / source files

- macros contains reusable macros
- seeds is for static files, data that doesn't change frequently
- snapshots: to create incremental models
- tests: dbt tests
