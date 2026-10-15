# Atividades Avaliativas - Microsserviços Java

Aluno: Gabriel Nogueira dos Santos - RA: 1127692

Projeto com o `product-api` (porta 8000) e o `currency-api` (porta 8100), usando Consul, PostgreSQL e Flyway.

## Como executar

1. Ter o PostgreSQL rodando com os bancos `db_product` e `db_currency`.
2. Rodar o `microservices/start_consul.bat`.
3. Subir o `currency-api` e depois o `product-api`.

## Testes

- Currency: `http://localhost:8100/currencies?source=USD&target=EUR`
- Product: `http://localhost:8000/products/1?targetCurrency=EUR`

## Atividades realizadas

1. Criei o currency-api, que informa a cotação entre moedas. Ele segue o mesmo modelo do product-api.
2. Fiz o product-api buscar a cotação no currency-api. Adicionei proteções para quando o currency-api falha ou demora: valor padrão, limite de tempo, novas tentativas, circuit breaker (pausa as chamadas depois de várias falhas) e cache.
3. Fiz o currency-api buscar a cotação no site do Banco Central, usando as mesmas proteções. Se o Banco Central falhar ou não tiver a cotação, ele usa o banco de dados local. Se não achar em nenhum dos dois, devolve erro 404.
