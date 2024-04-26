# Endpoints For Exchange Integration With CoinMarketCap

On this page, you can find a description of the endpoints that are necessary to integrate the exchange with CoinMarketCap. These endpoints must be specified in the "Five (5) API Endpoint URLs" field of the application form. Endpoints differ for different types of exchanges.

Most of the provided information can be found in [this document](https://docs.google.com/document/d/1S4urpzUnO2t7DmS_1dc4EL4tgnnbTObPYXvDeBnukCg/edit) created by the CoinMarketCap team.

## General requirements

To successfully integrate your exchange with CoinMarketCap, your API must meet the following standards:

1. A REST API with no API authentication required on endpoints.
2. Return all the data at once - No pagination
3. Full market queries available every 60 seconds. CoinMarketCap poll once per minute per market pair.
4. Dash, hyphen, or underscore base_quote pair notation. No base quote concatenation. 
5. Prices standardized to the quote currency.
6. Data available in JSON format
7. If applicable, turn Cloudflare security level to OFF for API endpoints.
8. Versioning required to avoid breaking changes (api/v1/asset, api/v2/asset, etc.)
9. Content encoding: gzip supported for optimized data transfer.
10. No region-blocked API endpoints or IP address whitelisting required, as CoinMarketCap risk losing data from the exchange if they change IPs for data collection in the future.

## Spot exchanges

To register a spot exchange you need to provide the following API endpoints.

### Summary endpoint

Provides information about all tickers and all market pairs on the exchange in a general form.

<details>
<summary><b>Endpoint response example</b></summary>

```json
[
  {
    "trading_pairs": "ETC_BTC",
    "last_price": 0.00067,
    "lowest_ask": 0.000681,
    "highest_bid": 0.00067,
    "base_volume": 1528.11,
    "quote_volume": 1.0282814600000003,
    "price_change_percent_24h": -1.3254786450662739,
    "highest_price_24h": 0.000676,
    "lowest_price_24h": 0.000666
  },
  {
    "trading_pairs": "XRP_BTC",
    "last_price": 0.0000203,
    "lowest_ask": 0.0000213,
    "highest_bid": 0.0000202,
    "base_volume": 350700,
    "quote_volume": 7.139649999999999,
    "price_change_percent_24h": -0.49019607843137253,
    "highest_price_24h": 0.0000204,
    "lowest_price_24h": 0.0000203
  }
]
```

</details>

<details>
<summary><b>Response fields description</b></summary>

| Name |   Type |   Status | Description |
|---|---|---|---|
| `trading_pairs` | `string` | Mandatory | Identifier of a ticker with a delimiter to separate base/quote, e.g. ADA-USD (Price of ADA is quoted in USD) |
| `base_currency` | `string` | Recommended | Symbol/currency code of base currency, eg. ADA |
| `quote_currency` | `string` | Recommended | Symbol/currency code of quote currency, eg. ADA |
| `last_price` | `decimal` | Mandatory | Last transacted price of base currency based on given quote currency |
| `lowest_ask` | `decimal` | Mandatory | Lowest Ask price of base currency based on given quote currency |
| `highest_bid` | `decimal` | Mandatory | Highest bid price of base currency based on given quote currency |
| `base_volume` | `decimal` | Mandatory | 24-hour volume of market pair denoted in BASE currency |
| `quote_volume` | `decimal` | Mandatory | 24-hour volume of market pair denoted in QUOTE currency |
| `price_change_percent_24h` | `decimal` | Mandatory | 24-hour % price change of market pair |
| `highest_price_24h` | `decimal` | Mandatory | Highest price of base currency based on given quote currency in the last 24-hours |
| `lowest_price_24h` | `decimal` | Mandatory | Lowest price of base currency based on given quote currency in the last 24-hours |
</details>

### Assets endpoint
  
Provides a detailed summary for each currency available on the exchange.

<details>
<summary><b>Endpoint response example</b></summary>

```json
{
  "BTC": {
    "name": "bitcoin",
    "unified_cryptoasset_id": 1,
    "can_withdraw": true,
    "can_deposit": true,
    "min_withdraw": 0.01,
    "max_withdraw ": 100,
    "maker_fee": 0.01,
    "taker_fee": 0.01
  },
  "ETH": {
    "name": "arbitrum",
    "unified_cryptoasset_id": 11841,
    "can_withdraw": false,
    "can_deposit": false,
    "min_withdraw": 10,
    "max_withdraw ": 0,
    "maker_fee": 0.01,
    "taker_fee": 0.01,
    "contractAddressUrl": "https://arbiscan.io/token/0x912CE59144191C1204E64559FE8253a0e49E6548,https://etherscan.io/token/0xB50721BCf8d664c30412Cfbc6cf7a15145234ad1,https://nova-explorer.arbitrum.io/token/0xf823C3cD3CeBE0a1fA952ba88Dc9EEf8e0Bf46AD",
    "contractAddress": "0x912CE59144191C1204E64559FE8253a0e49E6548,0xB50721BCf8d664c30412Cfbc6cf7a15145234ad1,0xf823C3cD3CeBE0a1fA952ba88Dc9EEf8e0Bf46AD"
  }
}
```

</details>

<details>
<summary><b>Response fields description</b></summary>

| Name |   Type |   Status | Description |
|---|---|---|---|
| `name` | `string` | Recommended | Full name of cryptocurrency. |
| `unified_cryptoasset_id` | `integer` | Recommended | Unique ID of cryptocurrency assigned by Unified Cryptoasset ID. |
| `can_withdraw` | `boolean` | Recommended | Identifies whether withdrawals are enabled or disabled. |
| `can_deposit` | `boolean` | Recommended | Identifies whether deposits are enabled or disabled. |
| `min_withdraw` | `decimal` | Recommended | Identifies the single minimum withdrawal amount of a cryptocurrency. |
| `max_withdraw` | `decimal` | Recommended | Identifies the single maximum withdrawal amount of a cryptocurrency. |
| `maker_fee` | `decimal` | Recommended | Fees applied when liquidity is added to the order book. |
| `taker_fee` | `decimal` | Recommended | Fees applied when liquidity is removed from the order book. |
| `contractAddressUrl` | `string` | Recommended | URL of contract address on each chain<br><br>https://arbiscan.io/token/0x912CE59144191C1204E64559FE8253a0e49E6548<br>https://etherscan.io/token/0xB50721BCf8d664c30412Cfbc6cf7a15145234ad1<br>https://nova-explorer.arbitrum.io/token/0xf823C3cD3CeBE0a1fA952ba88Dc9EEf8e0Bf46AD |
| `contractAddress` | `string` | Recommended | Contract address of the asset on each chain(e.g. 0x32353a6c91143bfd6c7d363b546e62a9a2489a20) |
</details>

### Ticker endpoint
  
Provides a 24-hour pricing and volume summary for each market pair available on the exchange.

<details>
<summary><b>Endpoint response example</b></summary>

```json
{
  "BTC_USDT": {
    "base_id": 1,
    "quote_id": 825,
    "last_price": 10000,
    "quote_volume": 20000,
    "base_volume": 2,
    "isFrozen": 0
  },
  "BNB_BTC": {
    "base_id": 1839,
    "quote_id": 1,
    "last_price": 0.00699900,
    "base_volume": 53819,
    "quote_volume": 99.3459,
    "isFrozen": 0
  }
}
```

</details>

<details>
<summary><b>Response fields description</b></summary>

| Name |   Type | Status | Description |
|---|---|---|---|
| `base_id` | `integer` | Recommended | The quote pair Unified Cryptoasset ID. |
| `quote_id` | `integer` | Recommended | The base pair Unified Cryptoasset ID. |
| `last_price` | `decimal` | Mandatory | Last transacted price of base currency based on given quote currency |
| `base_volume` | `decimal` | Mandatory | 24-hour trading volume denoted in BASE currency |
| `quote_volume` | `decimal` | Mandatory | 24-hour trading volume denoted in QUOTE currency |
| `isFrozen` | `integer` | Recommended | Indicates if the market is currently enabled (0) or disabled (1). |
</details>

### Orderbook endpoint
  
Provides a complete level 2 order book (arranged by best asks/bids) with full depth returned for a given market pair.

<details>
<summary><b>Endpoint parameters</b></summary>

| Name | Type | Status |   Description |
|---|---|---|---|
| `market_pair` | `string` | Mandatory |   A pair such as "ADA_WRT" |
| `depth` | `integer` | Recommended (used to calculate liquidity score for rankings) |  Orders depth quantity: [0,5,10,20,50,100,500]<br> Not defined or 0 = full order book<br>Depth = 100 means 50 for each bid/ask side. |
| `level` | `integer` | Recommended<br>(used to calculate liquidity score for rankings) |   Level 1 – Only the best bid and ask.<br>  Level 2 – Arranged by best bids and asks.<br>  Level 3 – Complete order book, no aggregation.<br>  |
</details>

<details>
<summary><b>Endpoint response example</b></summary>

```json
{
  "timestamp": 1585177482652,
  "bids": [
    [
      12462000,
      0.04548320
    ],
    [
      12457000,
      3.00000000
    ]
  ],
  "asks": [
    [
      12506000,
      2.73042000
    ],
    [
      12508000,
      0.33660000
    ]
  ]
}
```

</details>

<details>
<summary><b>Response fields description</b></summary>

| Name |   Type |   Status | Description |
|---|---|---|---|
| `timestamp` | `integer` <br>(UTC timestamp in ms) | Mandatory | Unix timestamp in milliseconds for when the last updated time occurred. |
| `bids` | `decimal` | Mandatory | An array containing 2 elements. The offer price and quantity for each bid order. |
| `asks` | `decimal` | Mandatory | An array containing 2 elements. The ask price and quantity for each ask order. |
</details>

### Trades endpoint
  
Provides data on all recently completed trades for a given market pair.

<details>
<summary><b>Endpoint parameters</b></summary>

| Name | Type | Status |   Description |
|---|---|---|---|
| `market_pair` | `string` | Mandatory |   A pair such as "ADA_WRT" |
</details>

<details>
<summary><b>Endpoint response example</b></summary>

```json
[   
   {         
      "trade_id":3523643,
      "price": 0.01,
      "base_volume": 569000,
      "quote_volume": 0.01000000,
      "timestamp": 1585177482652,
      "type":"sell"
   }
]
```

</details>

<details>
<summary><b>Response fields description</b></summary>

| Name |   Type | Status | Description |
|---|---|---|---|
| `trade_id` | `integer` | Mandatory | A unique ID associated with the trade for the currency pair transaction<br> Note: Unix timestamp does not qualify as trade_id. |
| `price` | `decimal` | Mandatory | Last transacted price of base currency based on given quote currency |
| `base_volume` | `decimal` | Mandatory | Transaction amount in BASE currency. |
| `quote_volume` | `decimal` | Mandatory | Transaction amount in QUOTE currency. |
| `timestamp` | `integer` <br>(UTC timestamp in ms) | Mandatory | Unix timestamp in milliseconds for when the transaction occurred. |
| `type` | `string` | Mandatory | Used to determine whether or not the transaction originated as a buy or sell.<br>  Buy – Identifies an ask was removed from the order book.<br>  Sell – Identifies a bid was removed from the order book. |
</details>

## Derivative exchanges

To register a derivative exchange you need to provide the following API endpoints.

### Contracts endpoint

Provides a summary of every single contract traded on the exchange. There should be a clear delineation between the contract type (e.g. perpetual, futures, options). Ideally, all information should be returned in a single endpoint.

<details>
<summary><b>Response fields description</b></summary>

| Name |   Type |   Status | Description |
|---|---|---|---|
| `ticker_id` | `string` | Mandatory | Identifier of a ticker with a delimiter to separate base/quote, eg. ADA-WRT |
| `base_currency` | `string` | Mandatory | Symbol/currency code of base pair, eg. ADA |
| `quote_currency` | `string` | Mandatory | Symbol/currency code of quote pair, eg. WRT |
| `last_price` | `decimal` | Mandatory | Last transacted price of base currency based on given quote currency |
| `base_volume` | `decimal` | Mandatory | 24-hour trading volume in BASE currency |
| `USD_volume`  | `decimal` | Recommended | 24-hour trading volume in USD |
| `quote_volume` | `decimal` | Mandatory | 24-hour trading volume in QUOTE currency |
| `bid` | `decimal` | Mandatory | Current highest bid price |
| `ask` | `decimal` | Mandatory | Current lowest ask price |
| `high` | `decimal` | Mandatory | Rolling 24-hour highest transaction price |
| `low` | `decimal` | Mandatory | Rolling 24-hour lowest transaction price |
| `product_type` | `string` | Mandatory | Futures, Perpetual, Options |
| `open_interest` | `decimal` | Mandatory | The number of outstanding derivatives  contracts that have not been settled |
| `open_interest_usd` | `decimal` | Mandatory | The sum of the Open Positions (long or short) in USD Value of the contract |
| `index_price` | `decimal` | Mandatory | Last calculated index price for underlying of contract |
| `creation_timestamp` | `integer` <br>(UTC timestamp in ms) | Mandatory <br>(only for expirable futures/options) | Start date of derivative (not needed for perpetual swaps) |
| `expiry_timestamp` | `integer` <br>(UTC timestamp in ms) | Mandatory<br>(only for expirable futures/options) | End date of derivative (not needed for perpetual swaps) |
| `funding_rate` | `decimal` | Mandatory | Current funding rate |
| `next_funding_rate` | `decimal` | Recommended | Upcoming predicted funding rate |
| `next_funding_rate_timestamp` | `integer` <br>(UTC timestamp in ms) | Mandatory | Timestamp of the next funding rate change |
| `maker_fee` | `decimal` | Recommended | Fees for filling a "maker" order (can be negative if rebate is given) |
| `taker_fee` | `decimal` | Recommended | Fees for filling a "taker" order (can be negative if rebate is given) |
</details>

### Contract specifications endpoint

Provides the specification of the contracts, mainly the pricing of the contract and its type (vanilla, inverse, or quanto). This endpoint  can be combined with the [contracts endpoint](#contracts-endpoint).

<details>
<summary><b>Response fields description</b></summary>

| Name | Data Type | Category | Description |
|---|---|---|---|
| `contract_type` | `string` | Mandatory | Describes the type of contract - Vanilla, Inverse or Quanto |
| `contract_price` | `decimal` | Mandatory | Describes the price per contract. |
| `contract_price_currency` | `string` | Mandatory | Describes the currency in which the contract is priced (e.g. USD, EUR, ADA, USDT) |
</details>

### Order book endpoint

Provides order book information with at least depth = 100 (50 each side) returned for a given market pair/ticker.

<details>
<summary><b>Response fields description</b></summary>

| Name | Data Type | Category | Description |
|---|---|---|---|
| `ticker_id` | `string` |   Mandatory | A pair such as "ADA-WRT", with a delimiter between different crypto-assets |
| `timestamp` | `integer` <br>(UTC timestamp in ms) |   Mandatory | Unix timestamp in milliseconds for when the last updated time occurred. |
| `bids` | `decimal` |   Mandatory | An array containing 2 elements. The offer price and quantity for each bid order |
| `asks` | `decimal` |   Mandatory | An array containing 2 elements. The ask price and quantity for each ask order |
</details>

## DEXes (Decentralized exchanges)

There is no strict endpoint format for DEX registration. You can check [DEXes section](https://docs.google.com/document/d/1S4urpzUnO2t7DmS_1dc4EL4tgnnbTObPYXvDeBnukCg/edit#bookmark=kix.5p33g7oj0og8) in CoinMarketCap API Description.

### WingRiders DEX Liquidity pools endpoint

This is the WingRiders DEX endpoint that was used to integrate with CoinMarketCap.

<details>
<summary><b>Endpoint response example</b></summary>

```json
{
  "ada_c0ee29a85b13209423b10447d3c2e6a50641a15c57770e27cb9d507357696e67526964657273": {
    "base_id": "ada",
    "base_name": "ADA",
    "base_symbol": "ADA",
    "quote_id": "c0ee29a85b13209423b10447d3c2e6a50641a15c57770e27cb9d507357696e67526964657273",
    "quote_name": "WingRiders Governance Token",
    "quote_symbol": "WRT",
    "last_price": "0.07844152527977104",
    "base_volume": "8894.632902",
    "quote_volume": "113028.163408"
  },
  "ada_25c5de5f5b286073c593edfd77b48abc7a48e5a4f3d4cd9d428ff93555534454": {
    "base_id": "ada",
    "base_name": "ADA",
    "base_symbol": "ADA",
    "quote_id": "25c5de5f5b286073c593edfd77b48abc7a48e5a4f3d4cd9d428ff93555534454",
    "quote_name": "USDT",
    "quote_symbol": "USDT",
    "last_price": "2.264542711518371",
    "base_volume": "29.603488",
    "quote_volume": "15.00000025"
  }
}
```

</details>

<details>
<summary><b>Response fields description</b></summary>

| Name | Data Type | Description |
|---|---|---|
| keys in the object | `string` | A pair of token IDs connected via an underscore |
| `base_id` | `string` | Id of the first token in the liquid pair |
| `base_name` | `string` | Name of the first token in the liquid pair |
| `base_symbol` | `string` | Symbol (ticker) of the first token in the liquid pair |
| `quote_id` | `string` | Id of the second token in the liquid pair |
| `quote_name` | `string` | Name of the second token in the liquid pair |
| `quote_symbol` | `string` | Symbol (ticker) of the second token in the liquid pair |
| `last_price` | `decimals` | The price at which the last exchange was made |
| `base_volume` | `string` | Volume of the first token in the liquid pair |
| `quote_volume` | `string` | Volume of the second token in the liquid pair |
</details>
