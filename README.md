# TesteDataEngineer
ETL Pipeline

## Planilha Users
Havia um campo de id_advisor nulo, como os demais dados são necessários caso o campo estivesse nulo o registro será descartado. Já o id_advisor como pode ser utilizando para uma transição, desligamento entre outros casos do negócio os campos nulos foram alterados para 0. A ideia inicial era alterar para NA de not assigned mas manter o campo como int traz ganhos de eficiência por isso essa anotação foi adotada. 

Deve ser feito o download do arquivo csv com os usuários e realizar o upload para o FileStore do Databricks 

## Planilha Advisors
Planilha com os dados consistentes assim como a anterior descartado registros nulos em qualquer campo e o detalhe do delimitador ser o ";" no lugar do padrão ",".

Também deve ser feito o download do arquivo csv com os usuários e realizar o upload para o FileStore do Databricks.


## Planilha com dados Legados
O link direto para o aquivo em .json deve ser inserido no campo url. Foi necessário transformar em rdd para facilitar a transformação para banco de dados relacional.  


## Tópico Kafka
O consumo do tópico transactions do Kafka foi feito em Scala com o spark streaming. Realizado o parse da string e salvo como tabela. 

# Tabelas disponíveis para queries SQL

| USERS | ADVISORS | LEGACY | KAFKA |
| :--------: | :---------: | :---------: | :---------: |
| <font size="1">USER_ID; DATE_REGISTER; NAME; ID_ADVISOR </font> |<font size="1"> ID_ADVISOR; NAME; GROUP; OFFICE</font>  |<font size="1">user_id; type; value; date_transaction</font>  | <font size="1">user_id; type_transaction; value_transaction; date_transaction </font> |

