# Web Socket Data

## Base Endpoint
| Environment | Base Endpoint |
|-|-|
|`Production`| please ask to colleague|
|`Development`| please ask to colleague|

## Understanding the Subscription Response
Every subscription will have a response.
```json
{
  "data": {}, #Data subscription
  "seq": 132 #sequent
}
```

## Public Channels
### Open Order
Fetches the orderbook with a depth of 50 orders per side

The data is ordered by price, order sell starting from lowest price and order buy starting from the highest price.

**Channel**
$SYMBOL.depth => eg. btcidr.depth

**Response Parameter**
|Parameter|Type|Comment|
|-|-|-|
|ask.order|float|Amount traded currency|
|ask.price|string|Order price|
|bid.order|float|Amount traded currency|
|bid.price|string|Order price|

**Example**
```json
{
  "data": {
    "ask": [
      {
        "order": 2.16143518,
        "price": "133610000"
      },
      {
        "order": 5,
        "price": "139000000"
      }
    ],
    "bid": [
      {
        "order": 1.22858981,
        "price": "130599000"
      },
      {
        "order": 3.84769292,
        "price": "129948000"
      }
    ]
  },
  "seq": 1
}
```

### Trade
Get real-time trading information.

**Channel**
$SYMBOL.trade => eg. btcidr.trade

**Response Parameter**
|Parameter|Type|Comment|
|-|-|-|
|amount|float|amount|
|direction|int| 1=buy |
|price|float|Order price|
|symbol|string|symbol|
|trade_time|int|trade time in unix timestamp|

**Example**
```json
{
  "data": {
    "amount": 348954,
    "direction": 1,
    "price": 133610000,
    "symbol": "btcidr",
    "trade_time": 1602575220
  },
  "seq": 8
}
```
### Tick
...

### Market Summaries
Get real-time summaries for all coin

**Channel**
market.summaries

**Response Parameter**
|Parameter|Type|Comment|
|-|-|-|
|prices_24h||amount|
|prices_24h.$symbol|int|last prices in 24 Hours|
|prices_7d|||
|prices_7d.$symbol|int|last prices in last 7 days|
|tickers|string|symbol|
|tickers.$symbol|||
|tickers.$symbol.close|int|closing price|
|tickers.$symbol.high|int|maximum price|
|tickers.$symbol.low|int|minimum price|
|tickers.$symbol.name|int|traded currency|
|tickers.$symbol.open|int|starting price|
|tickers.$symbol.server_time|int|trade time in unix timestamp|
|tickers.$symbol.volume|float|trading volume|

**Example**
```json
{
  "data": {
    "prices_24h": {
      "abyssidr": 102,
      "actidr": 72
    },
    "prices_7d": {
      "abyssidr": 102,
      "actidr": 72
    },
    "tickers": {
      "abyssidr": {
        "close": 102,
        "high": 102,
        "low": 102,
        "name": "abyss",
        "open": 102,
        "server_time": 1602578898,
        "volume": 0
      },
      "actidr": {
        "close": 72,
        "high": 73,
        "low": 72,
        "name": "act",
        "open": 80,
        "server_time": 1602578898,
        "volume": 184082.23124547
      }
    }
  },
  "seq": 1
}
```

### Market External
...
