# Bitinvestor Pricing API

## Table of Contents
- [Bitinvestor Pricing API](#bitinvestor-pricing-api)
  - [Table of Contents](#table-of-contents)
  - [Version](#version)
  - [API Information](#api-information)
    - [URL](#url)
    - [Body Format](#body-format)
  - [Definition](#definition)
  - [Note](#note)
  - [Supported Payment Methods](#supported-payment-methods)
  - [Supported Fiat Currencies](#supported-fiat-currencies)
  - [Supported Crypto Currencies](#supported-crypto-currencies)
  - [Response](#response)
    - [Definition:](#definition-1)

## Version
1.0.1

## API Information

### URL
`https\://eoats3bjlps5hvb.m.pipedream.net`

### Body Format

```json
{
  "payment_method": "creditcard",
  "fiat_currency": "EUR",
  "fiat_amount": 100, \(Optional\)
  "crypto_currency": "LTC",
  "crypto_amount": 1 \(Optional\)
}
```
## Definition

- `payment_method`: The selected payment method.
- `fiat_currency`: The selected fiat currency.
- `fiat_amount`: The fiat amount the customer wishes to pay.
- `crypto_currency`: The selected cryptocurrency.
- `crypto_amount`: If set, the calculation will be based on crypto amount instead of fiat amount.

**NB.** Body should either contain `fiat_amount` or `crypto_amount`. If both are set, `crypto_amount` will overwrite `fiat_amount`.

## Note

Minimum order amount is 7 EUR, 8 USD, or fiat currency equivalent.

## Supported Payment Methods

| Supported `payment_method` | Supported `fiat_currency`                                                                                                        |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| boleto                     | BRL                                                                                                                              |
| ideal                      | EUR                                                                                                                              |
| neosurf                    | EUR, DKK, GBP                                                                                                                    |
| dana                       | USD                                                                                                                              |
| promptpay                  | USD                                                                                                                              |
| pix                        | BRL                                                                                                                              |
| apple-pay                  | EUR, DKK, USD, GBP, SEK, PLN, KZT, NGN, RON, ZAR, UAH, TWD, THB, CZK, TRY, CHF, INR, BRL, HUF, CAD, AUD, MXN, IDR, JPY           |
| ovo                        | USD                                                                                                                              |
| kasikornbank               | USD                                                                                                                              |
| google-pay                 | EUR, DKK, USD, GBP, SEK, PLN, KZT, NGN, RON, ZAR, UAH, TWD, THB, CZK, TRY, CHF, INR, BRL, HUF, CAD, AUD, MXN, IDR, JPY           |
| spei                       | USD                                                                                                                              |
| netbankingindia            | USD                                                                                                                              |
| blik                       | PLN                                                                                                                              |
| mobilepay                  | DKK, EUR                                                                                                                         |
| airtm                      | USD                                                                                                                              |
| upi                        | USD                                                                                                                              |
| creditcard                 | EUR, DKK, USD, GBP, SEK, PLN, KZT, NGN, RON, ZAR, UAH, TWD, THB, CZK, TRY, CHF, INR, BRL, HUF, CAD, AUD, MXN, IDR, JPY           |
| caixa                      | USD                                                                                                                              |
| revolutpay                 | AED, AUD, BGN, CAD, CHF, CZK, DKK, EUR, GBP, HKD, HUF, ILS, ISK, JPY, MXN, NOK, NZD, PLN, RON, SEK, SGD, THB, TRY, USD, ZAR, JPY |
| astropay                   | USD                                                                                                                              |
| bank-transfer              | EUR, DKK, USD, GBP, CAD, SGD, HKD, CHF                                                                                           |
| mercadopago                | USD                                                                                                                              |
| jeton                      | EUR, GBP, USD, CAD                                                                                                               |
| tigerpay                   | JPY                                                                                                                              |
| papara                     | TRY                                                                                                                              |
| parazula                   | TRY                                                                                                                              |
| payfix                     | TRY                                                                                                                              |

## Supported Fiat Currencies

- CHF, GBP, RON
- CAD, USD, ZAR
- INR, PLN, UAH
- BRL, SEK, TWD
- HUF, SGD, MXN
- EUR, KZT, IDR
- HKD, NZD, AUD
- THB, CZK, TRY
- DKK, JPY

## Supported Crypto Currencies

- DOGE, LINK
- BCH, USDT
- BTC, USDC
- XRP, DAI
- LTC, ETH

## Response

```json
{
   "crypto_amount": "1.59397",
   "crypto_currency": "LTC",
   "crypto_unit_price": "60.30",
   "network_fee": "0",
   "fiat_amount_incl_fees": 100,
   "fiat_amount_excl_fees": "96.12",
   "fiat_currency": "EUR"
}
```
### Definition:
- `crypto_amount`: The crypto amount the customer would receive right now. Prices update every 10 sec.
- `crypto_currency`: The selected cryptocurrency.
- `crypto_unit_price`: The price for 1 of the selected cryptocurrency (In selected fiat).
- `network_fee`: The current network fee on the transaction (In selected fiat).
- `fiat_amount_incl_fees`: The amount the user will end paying after fees (In selected fiat).
- `fiat_amount_excl_fees`: The amount you should parse to our payment window (In selected fiat).
- `fiat_currency`: The selected fiat.


