# Dancespiele Worker

Dancespiele Worker is an cron job task application that add stop loss order in exchange crytoconcurrency platforms.

## How it works

First you need to set the increment percent of your current coins price that you wish to put a stop loss using [Dancespiele API](https://github.com/dancespiele/dancespiele_api).
For example imagine that you have `ETH` in [Kraken](https://www.kraken.com/) and its current price is `300 EUR` and you set in [Dancespiele API](https://github.com/dancespiele/dancespiele_api) the parameter `new_stop_loss` an increment of `0.20` (20%) then `ETH` increase to `370 EUR` (more than 20%) in the future, the Dancespiele Worker will add automatically a stop loss with a price of `354 EUR` (always 2% less than the stop loss set) guaranteeing a benefit of `54 EUR`, now you set the paremeter `next_stop_loss` to `0.10` (10%) and `ETH` increase to `410` (more than 10%), the application will set a stop loss of `398,86 €` based in the increment from the previous stop loss and it will continue setting new stop loss each time that price increase more than 10%.

## Requirements

* Rustup
* Account in some of the supported exchange platform (for now only support [Kraken](https://www.kraken.com/))

## How to run the application

1. Install [Dancespiele API](https://github.com/dancespiele/dancespiele_api)

2. `git clone https://github.com/dancespiele/dancaspiele_worker.git`

3. `cd dancespiele_worker`

4. set the .env file:

```
SLED_URL=[PATH WHERE YOU WANT THE SLED DB FILE. NOTICE THAT THE DB IS SHARING WITH Dancespiele API]
SECRET=[YOUR SECRET FOR THE API]
API_URL=[DANCESPIELE API URL]
EMAIL=[YOUR EMAIL TO GET THE NOTIFICATION OF THE ORDER]
TRADING_AGREEMENT=agree // FOR RESIDENTS IN GERMAN 
```

5. execute:

`cargo run`

6. Enjoy!

**Note:** Dancespiele worker will check the coin prices every 2 minutes in case that it add a stop limit order you will be notified by email if Dancespiele API and your email server are correctly set

## Do you like Dancespiele apps?
If you like Dancespiele apps, help us supporting the projects:
- [Github Sponsors](https://github.com/sponsors/dancespiele)

## License
Dancespiele Worker is [LICENSE PARITY](LICENSE-PARITY.md) and [LICENSE PATRON](LICENSE-PATRON.md) licensed. If you need a comercial license sponsor to Dancespiele in the right tier or contact to `spielcrypto@gmail.com`