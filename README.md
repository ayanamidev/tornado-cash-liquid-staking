# Liquid staking for Tornado Cash relayers

*Liquid staking* refers to the emission of a tokenized version of a locked token. Example: $CvxCrv is the liquid staking version of $CRV locked into Convex. $stETH is the liquid staking version of the $ETH staked by Lido on the beacon chain.

*tl;dr: Allow users to lock their tokens to a relayer in a decentralized way, in echange of a share of the fees collected and governance power over the relayer.*

## Why?
Currently, users wanting to participate in the protocol as a relayer need to lock forever a large amount of tokens, worth around 10,000$ at the time of writing. This creates a major barrier of entry, and an important risk, as you're effectively betting that the future revenues from the relaying will cover your initial investment.

Another limiting factor comes from the scoring system Tornado Cash uses to redirect the withdraw orders to relayers: the more you stake, the more you relay and thus the lower your income volatility is. This, in effect, gives a strong incentive to lock larger amounts, but at the same time, excludes smaller holders and thus reduces their implication in the protocol's internals. We can capture this effect in the revenue difference over time for relayer locking (~200% APR) and governance staking (~70% APR). 

## Proposal
This situation can be improved by creating a liquid staking framework for Tornado Cash relayers. Holders of $TORN would be allowed to delegate their tokens to a relayer, which would in exchange emit a liquid staking token representing the holder's share in the funds. This token can then be exchanged on the secondary market (with an AMM pair, for instance), be used to earn some of the relayer's fees, and participate in governance of the relayer, further decentralizing the protocol.

## Is there a risk of centralization from this?
Liquid staking has been criticized as increasing centralization in some cases, as the larger the general lock, the lower the income volatility and thus the general revenue model. While this is true, there are some remedies:
- Cap the amount allowed to be stacked by a single relayer, through governance.
- **Open-source** the code, so anyone can start a relayer liquid staking Dapp, leading to competition, innovation, and general improvement of the Tornado Cash protocol.

It the last case, you could see relayers' wars, such as what we see with the veToken economics, where relayers would have to position themselves and choose different strategies to compete for $Torn locks.

## Requirements

To keep up with Tornado Cash general ethic, the framework must be:
1. Trustless
2. Permissionless
3. Decentralized in term of governance

How does it translate in practice?

1. The general protocol will be governed by smart contracts, without any possibility for the relayer' operator to retain the funds.
2. The relayer operator can't prevent a user from locking funds, nor prevent a relay request that is submitted by the protocol.
3. Most aspects of the protocol must be modifiable, including the relayer operator. This means that if an operator stops running the relayer software on the behalf of the community, it would be possible to redirect the requests to a new operator, preventing any centralization of power.

## Economics

- The relayer asks for $TORN to be locked and emits a staked version of the tokens.
- A share of the relay fees is used buyback $TORN distributed to governance stakers.
- The profits are distributed to $TORN liquid staking token holders.
- The operator is incentivized to keep the infrastructure operational by taking a % of the the revenues.



