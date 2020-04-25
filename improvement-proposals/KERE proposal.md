# Kin Exchange Rewards Engine 1.0 (KERE) - (KIP)
The purpose of this document is to outline a proposed incentive structure known as the KERE. 

## Proposed by:
*WeviNest*

## Abstract
Liquidity is more important than ever for the success of the Kin project. Kin is now spent by over 4 million people per month and several new incentive structures have been created this year.  A Kin Exchange Rewards Engine aligns with the vision of the ecosystem as an incentive structure that allows all participants an equal shot at earning a stake of a significant reward. 

Exchanges are key ecosystem infrastructure and unlocking access is vital for project longevity. Alongside incentives for exchanges, the KERE has a real likelihood of generating interest from market makers and key influencers that have been out of reach. Recent efforts such as the Kin Community Rewards program point to the understanding that all pieces of the Kin ecosystem deserve to be incentivized.

In the spirit of creating additional incentive structures to support the Kin Ecosystem, the Kin Exchange Rewards Engine (KERE) will pay exchanges on a monthly/weekly basis for their liquidity contributions to the ecosystem. The proposal is a 500 Billion Kin Fund to incentivize liquidity: the Kin Exchange Reward Engine or KERE. A 10 year programme paying out 46 Billion Kin per year (~125,941,136 Kin/day;) to exchanges that include Kin as an active trading pair, with 8% set aside for new integration bonuses. The KERE will have 4 tracts: Volume, Derivatives Volume, Liquidity, and Holding in order to replicate the KRE 2.0 model and incentivize multiple kin-supporting verticals within exchanges.

## KERE 1.0
- 4 Tracts (Volume (42%), Derivatives Volume (20%), Liquidity (20%),   Holding (10%))
- 500 Billion Kin paid out over 10 years
- 8% set aside as Bonus Incentives to attract desirable exchanges
### Valid Volume Guidelines
- Accepted data sources: CoinGecko, CoinMarketCap, LiveCoinWatch, Link Oracles



## KERE Algorithm

**Payout:**

Across the four KERE tracks (Volume, Derivatives Volume, Liquidity, Hold), an exchange's (exchange i) total payout would be:

`Payout_i = Payout_volume_i + Payout_DerivativesVolume_i + Payout_Liquidity_i + Payout_hold_i`

Note that an exchange will only be rewarded KERE payouts for days where at least $1000 worth of Kin was traded on their respective exchange.

**Volume Tract:**  
`Let KERE_volume be the total amount of Kin paid to exchanges for the Volume track in a day.`

`Let volume_i be the total Kin trading volume in thousands of USD traded in a day by exchange i.`

`Payout_volume_i = min(KERE_volume * volume_i / sum for all exchanges i (volume_i), 20000 * volume_i)`

**Derivatives Volume Tract:**

`Let KERE_DerivativesVolume be the total amount of Kin paid to exchanges for the Derivatives Volume track in a day.`

`Let DerivativesVolume_i be the total Kin trading volume in thousands of USD traded in a day by derivatives exchange i.`

`The Payout_volume_i = min(KERE_DerivativesVolume * DerivaitvesVolume_i / sum for all derivatives exchanges i (DerivativesVolume_i), 10000 * DerivativesVolume_i)`

**Liquidity Tract:**

`Let KERE_Liquidity be the total amount of Kin paid to exchanges for the Liquidity track in a day.`

`Let Liquidity_i be the minimum Kin liquidity in thousands of USD available in a day by exchange i.`

`The Payout_volume_i = min(KERE_DerivativesVolume * DerivaitvesVolume_i / sum for all derivatives exchanges i (DerivativesVolume_i), 10000 * DerivativesVolume_i)`

**Holding Tract: the notation for the holding tract payout calculation is as follows**

`Let w_i = min(KERE_prior_payouts_i, minimum amount of Kin in KERE wallet during a day)`

`Payout_hold_i = min(w_i / sum(w_j for all exchanges j in A) * KERE_hold, w_i * 50% / 365.25)`

Note that an exchange’s KERE wallet will include both their KERE payout wallet and an optional verified cold-storage wallet they have provided.


**Bonus Incentives**

Finally, 40 Billion or 8% of the total KERE will be set aside to attract the initial investment in Kin liquidity from top exchanges as integration bonuses

8% Integration Bonuses: The first 8 of the 15 “desirable” exchanges to integrate Kin will be delivered 500 Million Kin.

A reasonable goal of any top-tier cryptocurrency with more than 5 million monthly users is to be listed on the best exchanges. Based on reputation and volume, 10 exchanges and 5 Futures exchanges will be targeted for integration bonuses by the KERE.

Exchanges: Binance, OKEx, Coinbase Pro, Kraken, Bittrex, Gemini, BitHumb, Huobi Global, BitStamp, BitFinex
Derivatives Market: OKEx (Futures), BitMex, Huobi DM, Binance (Futures), Bakkt

## Valid Volume Guidelines
<ol type="a">
  <li> Data Sources: Link Oracle, CoinMarketCap, CoinGecko, LiveCoinWatch </li>
</ol>

## Implementation
`KERE_total: This will be (46,000,000,000/365.25)` or ~125,941,136 Kin/day from January 2021 to December 2030.
The notation for KERE payout allocation will be as follows:

`KERE_volume = 0.457 * KRE_total`

`KERE_DerivativesVolume = 0.217 * KRE_total`

`KERE_Liquidity = 0.217 * KRE_total`

`KERE_DerivativesVolume = 0.109 * KRE_total`

**The KERE Carryover Pool**

Like in the KRE, Kin that was not paid out to developers will accumulate for future use. If there is unused payout for a particular KRE track this will become carryover pool added to future payouts averaged over the remainder of the year.

The notation for the KRE carryover pool calculation is as follows:  

Let `r` be the number of days left in 2020
Let `KRE_carryover` be the KRE carryover pool (initialized at 0)

Before a payout:
```
KRE_total = 500,000,000
If KRE_carryover > 0:
    KRE_total += [KRE_carryover / r]
```

After a payout:
```
If sum(Payout_i for all apps i in A) < KRE_total:
    KRE_carryover += KRE_total - sum(Payout_i for all apps i in A)
```

**Monopoly Clause** 

As in the KRE, I propose a continuation of the Monopoly Clause. Continually, it will apply separately to each KERE track to ensure that exchanges targeting a specific track will still be able to compete effectively.

No single exchange will receive more than 66.67% of the KRE payout for specific track for a given period and any exchange that would have received more than 50% of the track's payout will have their track payout adjusted.
No two exchanges will receive more than 90% of any KERE track's payout for a given period.
In both cases, residual payouts will be redistributed proportionally to other exchanges

Let `s_1, s_2, …, s_n` be the KRE track payout shares ordered by payout proportion in descending order before invoking the monopoly clause.
```
If (s_1 + s_2  > 0.90) or (s_1 > 0.5):
    If s_1 > 0.5:
        s_1' = 0.5 + ((s_1 - 0.5) / 0.5) * (2/3 - 1/2)
    Else:
        s_1' = s_1
    If s_1' + s_2  > 0.90 then:
        s_2' = s_2 / (s_1+s_2) * 0.9
    Else:
    	s_2' = s_2
    s_1’ = minimum(s_1' / (s_1'+s_2) * 0.9, s_1')
    If s_2’ != s_2:
        For i = 3 to n:
            s_i’ = s_i / (sum from i = 3 to n of s_i) * 0.1
    Else:
        For i = 2 to n:
            s_i’ = s_i / (sum from i = 2 to n of s_i) * (1 - s_1')
	Exchanges are paid out based on s_i’
Else:
	Exchanges are paid out based on s_i
 ```

**Example 1:**  
Payout track shares before clause: `{0.35, 0.3, 0.2, 0.15}`  
Payout track shares after clause: `{0.35, 0.3, 0.2, 0.15}`  
Reasoning: Clause does not apply

**Example 2:**  
Payout track shares before clause: `{0.90, 0.05, 0.03, 0.02}`  
Payout track shares after clause: `{0.633, 0.183, 0.11, 0.073}`  
Reasoning: 2.i.1 applies

**Example 3:**  
Payout track shares before clause: `{0.50, 0.45, 0.03, 0.02}`  
Payout track shares after clause: `{0.474, 0.426, 0.06, 0.04}`  
Reasoning: 2.i.2 applies

**Example 4:**  
Payout track shares before clause: `{0.55, 0.44, 0.01}`  
Payout track shares after clause: `{0.486, 0.414, 0.06, 0.10}`  
Reasoning: Both 3.1 and 3.2 apply, first `0.55` is changed to `0.517` by 3.1, then `0.517` and `0.44` are changed to by 2.a.2.

While `66.67%` seems high for a single exchange to receive, we do not want to discourage strong exchanges from entering the ecosystem. Moreover, because any exchange with payout shares above `50%` will be adjusted, most of the time the top exchange will receive much less than `66.67%`:


Payout track shares before clause | Payout track shares after clause
--------------------------- | --------------------------
`50%` | `50%`
`60%` | `53.33%`
`70%` | `56.67%`
`80%` | `60%`
`90%` | `63.33%`
`95%` | `65%`

This table assumes that 2.i.2 does not apply.
