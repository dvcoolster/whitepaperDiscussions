# Whitepaper Discussions
Short notes, links and reference for internal team discussions @MerkleLab related to Whitepapers.

## Discusion Details
Provide an overview of how to use this document

## Projects
- AirSwap


| **Name**| AirSwap|
|:--------|:--------|
| **Token**:| AST|
|[WhitePaper](https://swap.tech/whitepaper/)|[CoinMarketCap](https://coinmarketcap.com/currencies/airswap/)|
|**Date**:| 17th January 2018|
|Company   |ConsenSys   |
|Founder   |Michael Oved, Don Mosites   |

**Table of Contents**:
1. [Summary](#1. Summary)
1. Introduction
    - Orderbook
    - Peer to Peer
    - **Swap Protocol**
1. Peer Protocol
1. Indexer Protocol
1. Oracle Protocol
1. Smart Contract


### 1. Summary
![Summary][1]

### 2. Introduction
Overview: Alternative to Blockchain Orderbook by specifying a set of protocols

#### Orderbook

- Do not scale well
- Miner manipulation is possible
- Lots of other problems as well!

So, now come as saviour!

#### Peer to Peer

- Scale, because they’re always done
- No cancel, lightweight, private negotiation, fair.
- They’re awesome overall!
- Need to beat AI man! Come together, world peace.

_[Background Music] Hero Entry!_

#### Swap!

Foundation Peer Protocol for Asset Exchange, _Go Team Ethereum!_


### 3. Peer Protocol
![Swap Introduction][2]

**Order API** is high level right now. Further details would be discussed in future papers.

`getOrder` & `provideOrder`

**Quotes API** is also similar, but for price exchange and not executable order. Can be executed if conditions are met later.

`getQuote` & `provideQuote`

### 4. Indexer Protocol: FindEther

![Indexer Introduction][3]

**Indexer API** manages intent to trade using the following commands between the peers and an indexer.

- `addIntent(makerToken, takerTokens)`
- `removeIntent(makerToken, takerTokens)`
- `getIntent(makerAddress)`
- `findIntent(makerToken, takerToken)`
- `foundIntent(makerAddress, intentList)`

### 5. Oracle Protocol: coinbase_prices

Use external sources for determining fair prices of trade.

![Oracle][4]

Similar for Taker Oracle.

**Oracle API** is `getPrice`, `providePrice`. Broadly just a source, like coinbase_prices.

### 6. Smart Contract

`fillOrder(makerAddress, makerAmount, makerToken, takerAddress, takerAmount, takerToken, expiration, nonce, signature)`

`cancelOrder`: Before being filled, it fills the order, so later it’s already filled.

Event broadcast: ``‘filled’`` and `‘cancelled’`.

_Transfer Ether_: if null takerToken address (0x0) then it will transfer ether in the function call on behalf of the taker to the maker

[Summary](# 1. Summary)

[1]: https://preview.ibb.co/ca2V7R/Screen_Shot_2018_01_17_at_8_27_49_PM.png
[4]: https://image.ibb.co/nrYEZ6/Screen_Shot_2018_01_17_at_8_19_28_PM.png
[3]: https://image.ibb.co/hWk6gm/Screen_Shot_2018_01_17_at_8_01_27_PM.png
[2]: https://image.ibb.co/c0jz1m/Screen_Shot_2018_01_17_at_7_31_55_PM.png
