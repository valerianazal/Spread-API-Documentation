---
title: Spread API Documentation

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - javascript: javaScript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>
includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Spread API
---

# Spread API

Bienvenido a la documentación de ✨Spread API✨
## Get All Market Spreads

```javascript
const router = require('express').Router();

router.get('/spread');
```

> Esta llamada retorna un JSON con el siguiente formato:

```json
{
  "All Markets Spread": [
    90392999,
    1100937052,
    9901700,
    ...
  ]
}
```

Esta llamada permite acceder al spread de todos los mercados en la API de Buda.

### HTTP Request

`GET http://localhost:3000/api/markets/spread`

### Response Details

Key | Tipo | Description
--------- | ------- | -----------
All Markets Spread | [array] | Spread de cada mercado

## Get a Specific Market Spread

```javascript
const router = require('express').Router();

const market_id = 'btc-clp';
router.get('/:marketId/spread');
```

> Esta llamada retorna un JSON con el siguiente formato:

```json
{
  "Market Spread": 90392999
}
```

Esta llamaada permite acceder al spread de un mercado específico.

### HTTP Request

`GET http://localhost:3000/api/markets/<marketId>/spread`

### URL Parameters

Parameter | Description
--------- | -----------
marketId | Identificador del mercado del que se quiere el spread

### Response Details

Key | Tipo | Description
--------- | ------- | -----------
Market Spread | [int/double] | Spread del mercado con identificador `marketId`

## Post Market Spread

```javascript
const router = require('express').Router();

const market_id = 'btc-clp';
router.post('/:marketId/spread');
```

> Esta llamada retorna un JSON con el siguiente formato:

```json
{
  "Status": "File Updated"
}
```

Esta llamada actualiza el archivo `spread.json`.

### HTTP Request

`POST http://localhost:3000/api/markets/<marketId>/spread`

### URL Parameters

Parameter | Description
--------- | -----------
marketId | Identificador del mercado del que se quiere guardar el spread

### Response Details

Key | Tipo | Description
--------- | ------- | -----------
Status | [string] | File Updated

## Get Market Polling

```javascript
const router = require('express').Router();

const market_id = 'btc-clp';
router.get('/:marketId/polling');
```

> Esta llamada retorna un JSON de alerta con el siguiente formato:

```json
{
  "[ALERT]": "Spread does not match"
}
```

Esta llamada retorna una alerta si el spread actual es diferente al guardado en `spread.json`. Si es el mismo, retorna estado `200`.

### HTTP Request

`GET http://localhost:3000/api/markets/<marketId>/polling`

### Query Parameters

Parameter | Description
--------- | -----------
marketId | ID del mercado del que se quiere comparar el spread con el guardado