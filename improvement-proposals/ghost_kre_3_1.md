# Kin Improvement Proposal - KRE v3.1
The purpose of this document is to propose an emergency temporary KRE payout calculation adjustment.

## Proposed by: Ghost_Type

## Abstract
Currently, the KRE pays developes in Kin based on USD prices, calculated based on a 7 day average of closing price on CoinMarketCap. While the KRE should seek to stabilize and broaden this calculation to a higher time-frame as the market matures,
this system was not optimized for extreme price volatility, and CMC is particularly ill-suited due to the inclusion and exclusion of highly volalite markets. In fact, this was predicted by Kik Engineering and is noted in [current-KRE](current-KRE.md):

*In the event of a dramatic price change (+/- 50% as defined by a 7-day average of closing price on CoinMarketCap), this frequency of recalibration can be more dynamic and can be addressed through a proposal to the Foundation.*

In the past week, Kin grew by more than 600%. This has resulted in massive payouts based on past prices that have stifled the potential economic growth of Kin. As such, this proposal seeks to outline a recalibration, along with a novel adjustment to the method of calculating the price that is designed to mitigate economic impact.

## Summary of Improvements
1. KRE Algorithm Updates
- *Temporary real-time price calculation: While the opposite direction of the long-term payout objectives of the KRE, as the "central bank" of the Kin Economy, the Kin Foundation should adjust price calculation to be based on more recent data, for as long as they forecast potential high volaility.*
- *Single data point price calculation: As volatility increases and the reliability of coinmarketcap decreases, the closing prices become less relevant an indicator of the economy at time of payout than originally intended. As such, prices calculation should be optimized for the mitigation of economic damage.*


## KRE Algorithm Updates

<ol type="a">
  <li>Temporary Real-Time Price Calculation</li>
<i>KRE payout amounts should be calculated using prices from the same week as payout, up to time of payout.</i>

<li>Single Price Point Price Calculation</li>
<i>Kin price for payout calculation should be based on a single data point, proposed here to be the lowest 7 day price of Kin that week. The data should be based on an single exchange with the most liquidity and/or volume, as CoinMarketCap is affected by extreme moves on unreliable exchanges.</i>
</ol>

## Implementation
It is recommended that this KIP be expedited to be approved by the Kin Foundation and enacted immediately, possibly along with KRE 3.0 if appropriate.
