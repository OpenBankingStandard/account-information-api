---
title: Open Banking API
---

# The Open Banking API

Hello world.

# Customers

## Get Customer

```json
{
  "full_name": "Fluffums",
  "date_of_birth": "2016-02-20",
  "_links": {
    "v1:addresses": { "href": "..." },
    "v1:accounts": { "href": "..." }
  }
}
```

`GET /customers/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the customer

# Accounts

## List Customer Accounts

```json
{
  "_embedded": {
    "v1:accounts": [
      {
        "customer_id": "26125952-a1cc-4c9b-91a1-99062192f422",
        "name": "Account name",
        "number": "123456",
        "sort_code": "42-42-42",
        "type": "current",
        "iban": "123080FZAFA9124AZE",
        "balance_cents": 1337133713371337,
        "currency": "GBP",
        "_links": {
          "self": { "href": "..." },
          "v1:transactions": { "href": "..." },
          "v1:cards": { "href": "..." }
        }
      }
    ]
  }
}
```

`GET /customers/:id/accounts`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the customer

## Create Account

```json
{
  "customer_id": "26125952-a1cc-4c9b-91a1-99062192f422",
  "name": "Account name"
}
```

`PUT /accounts/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the account

## Get Account

```json
{
  "customer_id": "26125952-a1cc-4c9b-91a1-99062192f422",
  "name": "Account name",
  "number": "123456",
  "sort_code": "42-42-42",
  "type": "current",
  "iban": "123080FZAFA9124AZE",
  "balance_cents": 1337133713371337,
  "currency": "ISO_4217 (ie. GBP)",
  "_links": {
    "v1:transactions": { "href": "..." },
    "v1:cards": { "href": "..." }
  }
}
```

`GET /accounts/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the account

# Cards

## List Account Cards

```json
{
  "_embedded": {
    "v1:cards": [
      {
        "account_id": "33325952-a1cc-4c9b-91a1-99062192f422",
        "last_4": "1234",
        "name_on_card": "Legit Larry",
        "_links": {
          "self": { "href": "..." },
          "v1:transactions": { "href": "..." },
          "v1:address": { "href": "..." }
        }
      }
    ]
  }
}
```

`GET /accounts/:id/cards`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the account

## Create Card

```json
{
  "account_id": "33325952-a1cc-4c9b-91a1-99062192f422",
  "name_on_card": "Legit Larry"
}
```

`PUT /cards/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the card

## Get Card

```json
{
  "account_id": "33325952-a1cc-4c9b-91a1-99062192f422",
  "last_4": "1234",
  "name_on_card": "Legit Larry",
  "expiry": "2018-12",
  "blocked_at": null,
  "_links": {
    "v1:transactions": { "href": "..." },
    "v1:address": { "href": "..." }
  }
}
```

`GET /cards/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the card

# Addresses

## List Customer Addresses

```json
{
  "_embedded": {
    "v1:addresses": [
      {
        "customer_id": "32325952-a1cc-4c9b-91a1-99062192f422",
        "first_line": "100 Dinosaur Lane",
        "city": "City of London",
        "region": "Greater London",
        "postcode": "EC1 8EY",
        "country": "GB",
        "lng": 51.2222,
        "lat": -0.0922222,
        "expiry": "2018-12",
        "blocked": false,
        "_links": {
          "self": { "href": "..." }
        }
      }
    ]
  }
}
```

`GET /customers/:id/addresses`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the customer

## Create Address

```json
{
  "customer_id": "32325952-a1cc-4c9b-91a1-99062192f422",
  "name": "home",
  "address": "100 Dinosaur Lane, Greater London, EC2 8EY"
}
```

`PUT /addresses/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the address

## Get Address

```json
{
  "customer_id": "32325952-a1cc-4c9b-91a1-99062192f422",
  "name": "home",
  "formatted_address": "100 Dinosaur Lane, Greater London, EC2 8EY",
  "lng": 51.2222,
  "lat": -0.0922222
}
```

`GET /addresses/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the address

# Transactions

## List Account Transactions

```json
{
  "_embedded": {
    "v1:transactions": [
      {
        "id": "56325952-a1cc-4c9b-91a1-99062192f422",
        "amount": -900,
        "currency": "GBP",
        "description": "ROFL STEVIE",
        "balance_cents": 123123,
        "created_at": "2016-02-20T13:44:19Z",
        "settled_at": "2016-02-22T13:44:19Z",
        "decline_code": null,
        "_links": {
          "self": { "href": "..." }
        }
      }
    ]
  },
  "_links": {
    "next": { "href": "..." },
    "prev": { "href": "..." }
  }
}
```

`GET /accounts/:id/transactions`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the account

### Pagination

next & prev links

## Search Transactions

```json
{
  "_embedded": {
    "v1:transactions": [
      {
        "id": "56325952-a1cc-4c9b-91a1-99062192f422",
        "amount": -900,
        "currency": "GBP",
        "description": "FOO BAR BAZ QUX",
        "balance_cents": 123123,
        "created_at": "2016-02-20T13:44:19Z",
        "settled_at": "2016-02-22T13:44:19Z",
        "decline_code": null,
        "_links": {
          "self": { "href": "..." }
        }
      }
    ],
    "_links": {
      "next": { "href": "..." },
      "prev": { "href": "..." }
    }
  }
}
```

`GET /accounts/:id/transactions/search`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the account

### Query Parameters

Parameter | Description
--------- | -----------
q | Query string (optional)
from | from date (optional)
to | to date (optional)

### Pagination

next & prev links

## Get Transaction

```json
{
  "id": "56325952-a1cc-4c9b-91a1-99062192f422",
  "amount": -900,
  "currency": "GBP",
  "description": "FOO BAR BAZ QUX",
  "balance_cents": 123123,
  "created_at": "2016-02-20T13:44:19Z",
  "settled_at": "2016-02-22T13:44:19Z",
  "decline_code": null
}
```

`GET /transactions/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the transaction

# Payments

## Make a payment

```json
{
  "account_id": "33325952-a1cc-4c9b-91a1-99062192f422",
  "amount": 1337,
  "reference": "SRS BSNSS",
  "counterparty": {
    "account_name": "DODGEY DAVE",
    "account_number": "...",
    "sort_code": "..."
  }
}
```

`PUT /payments/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the payment

## Get a payment

```json
{
  "account_id": "33325952-a1cc-4c9b-91a1-99062192f422",
  "amount": 1336,
  "reference": "SRS BSNSS",
  "counterparty": {
    "account_name": "DODGEY DAVE",
    "account_number": "...",
    "sort_code": "..."
  },
  "created_at": "2016-02-22T13:44:19Z",
  "settled_at": null
}
```

`GET /payments/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the payment
