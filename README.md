# saturn2022-tools

Measurement scripts for [saturn2022](https://saturn2022.com). Every
number in the whitepaper and the site comes from one of these; each is a small
Node program that reads Robinhood Chain directly and prints a table. No
dependencies, no keys, no account, no wallet.

The reader disagrees with a number by running the script that produced it.

```
chain id   4663
rpc        https://rpc.mainnet.chain.robinhood.com
explorer   https://robinhoodchain.blockscout.com
```

## The scripts

```
01-chain.mjs             block time, median fee, revert rate
02-stock-tokens.mjs      the scaled-amount extension and its dividend multipliers
03-how-stocks-trade.mjs  decoded from live fills: signed quotes, one prop rail
04-cost-of-pushing.mjs   what it costs a contract to hand assets to every holder
05-cost-of-not-pushing.mjs   the same payout, computed from the receipts
06-stock-market-size.mjs the on-chain equity market, sized before building on it
07-calibrate-thresholds.mjs  each feed's own publish threshold, from its own rounds
08-dataset.mjs           round history for every feed, saved to out/rounds.json
09-validate.mjs          the passage estimator against realized volatility
10-heat.mjs              does the tape run hot before it moves
11-backtest.mjs          the vault's economics, per markup and per tenor
```

Also:

```
rpc.mjs                  the toolkit: json-rpc, eth_call, decoders, table
tokens.mjs               the stock token registry
out/rounds.json          the round dataset the estimators run over
```

## Running one

```
$ node scripts/01-chain.mjs

block time    0.1007 s   (9.9 blocks per second)
median fee    $0.0078
reverted      7% to 13% of transactions, depending on the sample
```

## The paper

The estimator these scripts validate is the subject of a working paper:
[saturn2022-paper](https://github.com/Saturn2022Fi/saturn2022-paper). Every
figure in it is reproduced here.
