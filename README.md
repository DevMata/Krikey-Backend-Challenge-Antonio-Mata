<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo_text.svg" width="320" alt="Nest Logo" /></a>
</p>
  
# Description

Krikey Backend Challenge

## Installation

```bash
$ volta install node
$ volta install yarn
$ yarn install
```

## Running the app

```bash
# development
$ yarn run start

# watch mode
$ yarn run start:dev

# production mode
$ yarn run start:prod
```

## Test

```bash
# unit tests
$ yarn run test

# e2e tests
$ yarn run test:e2e

# test coverage
$ yarn run test:cov
```

# Solution

## Part 1: SQL Challenge

1. Who are the first 10 authors ordered by date_of_birth?

```sql
SELECT * FROM authors ORDER BY date_of_birth ASC LIMIT 10
```

2. What is the sales total for the author named “Lorelai Gilmore”?

```sql
SELECT a.name AS author_name, SUM(si.item_price*si.quantity) AS sales_total FROM sales_items si
INNER JOIN books b ON si.book_id = b.id
INNER JOIN authors a ON b.author_id = a.id
WHERE a.name = 'Lorelai Gilmore'
```

3. What are the top 10 performing authors, ranked by sales revenue?

```sql
SELECT a.id AS author_id, a.name AS author_name, SUM(si.item_price*quantity) AS revenue FROM sales_items si
INNER JOIN books b ON si.book_id = b.id
INNER JOIN authors a ON b.author_id = a.id
GROUP BY a.id
ORDER BY revenue DESC
LIMIT 10
```

## Part 2: API Endpoint to get top performing authors

The API was built with NestJs. The following are required env vars to run the project

| Environment Variable Key | Environment Variable Value         |
| ------------------------ | ---------------------------------- |
| DB_CONNECTION            | postgres                           |
| DB_HOST                  | localhost                          |
| DB_USERNAME              | your username                      |
| DB_PASSWORD              | your password                      |
| DB_PORT                  | 5432                               |
| DB_NAME                  | postgres                           |
| DB_SCHEMA                | public                             |
| DB_MIGRATIONS_TABLE_NAME | migrations                         |
| DB_MIGRATIONS            | dist/migrations/\*.js              |
| DB_MIGRATIONS_DIR        | migrations                         |
| DB_MIGRATIONS_RUN        | true                               |
| DB_SEEDS                 | src/seeds/\*_/_{.ts,.js}           |
| DB_FACTORIES             | src/seeds/factories/\*_/_{.ts,.js} |
| PORT                     | 3000                               |
| PREFIX                   | api/v1                             |
