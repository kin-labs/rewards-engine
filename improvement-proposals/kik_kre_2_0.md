## Kin Improvement Proposal - KRE V2.0
The purpose of this document is to outline a proposed new version of the KRE Algorithm

## Proposed by: Kik Interactive Inc. 

## Abstract
In the [KRE V1.1](kik_kre_1_1.md) Kin Improvement Proposal (KIP) we identified vulnerabilities in the existing [KRE V1.0](https://github.com/kinecosystem/rewards-engine/blob/master/accepted/KRE-v1.0.md) algorithm and made recommendations for an immediate adoption of these new principles. The KRE V1.0 was simple. As the first iteration it was important to make it (1) easy to understand and (2) incentivize the initial growth of the economy. Since launching KRE V1.0 the number of developers building in the ecosystem has more than tripled, and the number of people spending Kin per month has gone from 80k to 1.0MM as of November 19, 2019. Now that the ecosystem is reaching a state of maturity, we believe that the incentive protocol should also evolve. This KRE V2.0 proposal is being put forth for a January 1, 2020 kick off. This will give developers time to adapt their use cases to optimize for the updated incentives.

## Summary of Improvements
For the Kin economy to grow, Kin needs to grow in value. The value of Kin is driven by supply and demand. Today the KRE is increasing the supply of Kin very few people are buying Kin. That is pushing the value of Kin lower. While the price of Kin is purely a function of the free market, and no one can control or guarantee it, it is paramount that the economics behind the issuance of this digital currency are designed in such a way that the participants of the economy can prosper, wherever possible.

There are three key challenges with the existing algorithm: 
1. There is insufficient incentive to get individual users to spend more Kin
1. There is insufficient incentive to get users buying Kin
1. There is insufficient incentive for developers to hold Kin

The following proposal has three tracks to address these challenges:
1. Update to the existing DAS track to include a payout structure proportional to amount of Kin spend
1. Introduction of a new, separate track to incentivize buying
1. Introduction of a developer holding track

## 1. Spend
The current KRE algorithm has one track incentivizing developers to grow the number of daily active spenders in their app. This got people into the economy and using Kin on a daily basis. What the current DAS algorithm does not account for is the amount of Kin people are spending. The more Kin that users are spending, the higher the demand will be, which should translate to a higher value of Kin. Given that, we are proposing that the payout structure for the spend track be proportional to the amount of Kin that a user is spending with a cap on payout per DAS threshold. In order to give developers time to adapt to the updated spend amounts, in January of 2020 we will award up to 15,000 Kin for any daily active spender. This is roughly what developers are awarded in 2019 at the time of writing.

The notation of the Spend algorithm for January will then be:  
`Let KRE_spend be the total amount of Kin paid to developers for the Spend track in a day.`  
`Let spend_i be the number of users who spend Kin in a day in app i.`  
`Payout_spend_i = min(KRE_spend * spend_i / sum for all apps i (spend_i), 15000 * spend_i)`  

Below is the recommended schedule of payout proportions starting Feb 1, 2020: 

Kin spent per DAS per day | 1 - 9 Kin spent per day | 10 - 99 Kin spent per day | 100 - 999 Kin spent per day | 1,000+
--------------------------|-------------------------|---------------------------|-------------------------|-------
Max Payout per spender | 3,000 Kin | 6,000 Kin | 12,000 Kin | 30,000 Kin

It is recommended that the thresholds and maximum payout amounts are recalibrated on a quarterly basis to align with roughly $0.15 for a 1,000+ Kin spender (assuming the price of Kin is still below $0.15 for 1000 Kin). In the event of a dramatic price change (+/- 50% as defined by a 7-day average of closing price on CoinMarketCap), this frequency of recalibration can be more dynamic and can be addressed through a proposal to the Foundation.

The notation of the Spend algorithm going forward will then be:  
`Let KRE_spend be the total amount of Kin paid to developers for the Spend track in a day.`  
`Let spend_i_1 be the number of users who spend 1-9 Kin in a day in app i.`  
`Let spend_i_10 be the number of users who spend 10-99 Kin in a day in app i.`  
`Let spend_i_100 be the number of users who spend 100-999 Kin in a day in app i.`  
`Let spend_i_1000 be the number of users who spend 1000 or Kin in a day in app i.`  
`Then spend_i = spend_i_1 + 2*spend_i_10 + 4*spend_i_100 + 10*spend_i_1000`  
`Payout_spend_i = min(KRE_spend * spend_i / sum for all apps i (spend_i), 3000 * spend_i)`  

## 2. Buy
The value of Kin is driven by the amount of buy-side pressure relative to the sell-side pressure. In the simplest form, if more people want to buy Kin than people want to sell Kin then Kin is more valuable. In the early stages of the ecosystem there were no easy ways for users to buy Kin and use in app, so the initial incentives were tied to spending. Spending is the closest proxy to demand of a currency - the more someone is spending it, the more they will demand the currency. As the ecosystem has matured there are now easier ways to enable users to buy Kin. Given that, we are proposing a new track within the KRE to reward developers to the extent that they get users buying Kin in their app. 

Buy demand generated by ecosystem apps can be roughly thought of as:  
`Sum of User Wallet Increases - Sum of Wallet Decreases - Sum of Prior KRE Payouts + Prior KRE Payouts Held`

This equation approximates buy demand at the aggregate rather than tracking individual purchases. The assumption inherent is that if this equation is positive, there would necessarily need to be buy demand generated in order for a user’s wallet to increase. This could be a user buying, a developer buying and giving to users, or an advertiser buying Kin to pay users. In order to allow developers to adjust to this new buy demand track (and make it feasible to start receiving payouts in this track at a later date) only prior KRE payouts in the buy demand track will be counted against a developer's buy demand.

More formally:  
`Let KRE_buy be the total amount of Kin paid to developers for the Buy track in a day`  
`Let w_increase_i be the summed user wallet balance increase in app i over the lifetime of the KRE`  
`Let w_decrease_i be the summed wallet balance decrease in app i over the lifetime of the KRE`
`w_i is the amount of Kin held in a developer's holding wallet from prior KRE payouts. This is properly defined in the Holding section` 
`Let KRE_prior_buy_demand_payouts_i be the summed Kin paid to app i over the lifetime of the KRE (including grants)`  

We define `buy_demand_i` for app `i` as:  
`buy_demand_i = max(w_increase_i - w_decrease_i - KRE_prior_buy_demand_payouts_i + minimum(w_i, KRE_prior_buy_demand_payouts_i), 0)`

Then the buy payout for app i is:  
`Payout_buy_i = min(KRE_buy * buy_demand_i / (sum for all apps j buy_demand_j), buy_demand_i)`

Another option considered to measure buy demand was to tag individual transactions, or only count purchases generated through specific buy/sell gateways. The option recommended above is less discriminatory to specific buy/sell gateways and requires less data collection. For this reason, it is recommended to observe buy demand in the aggregate. 

One obvious vulnerability in observing the data in aggregate instead of tracking the source of individual transactions is the ability for app developers to send KRE earned Kin between apps, showing a net increase in wallet balances without creating any buy demand. Apps developed by the same parent company will be given a single KRE payout based on the total use of all of the apps. In the near term, this is a design flaw in the algorithm that we recommend is allowed. There is value in users moving between apps, this was denoted at “tourism” in previous incentive models. The Buy Demand Algorithm will stand in for a tourism incentive in the near term. In the future, there may be more specific stipulations made on sources of wallet increases. 

## 3. Hold
As noted above, the value of Kin is a function of the amount of Kin being bought relative to the amount of Kin being sold. Each KRE payout increases the available Kin to be sold. While the Spend and Buy tracks incentivize an increase in buy-pressure, we are also proposing an incentive tied to a reduction in sell-pressure in the form of a holding reward for developers. 

There are two options we have considered for an implementation of the holding reward:

**Option 1 - Fixed-Term**  
The fixed-term option would have developers hold their KRE payouts for a discrete period of time and receive an additional payout at the end of the hold period for doing so. The Foundation would set the time and incentive parameters and each developer would have the option to opt-in with Kin earned through the KRE. In the future this could be operated via a smart contract; today developers would send the Kin to a public address that they control. If at the end of the term the Kin has not moved, the reward would then be sent to that same address. 

The notation for the holding payout calculation is as follows:
`Let KRE_hold be the total amount of Kin paid to developers for the Hold track in a day.`  
`Let b_ij be the amount that app i wants to purchase for their jth hold.`  
`a) 3  month hold ->  We define b'_ij = b_ij`  
`b) 6  month hold ->  We define b'_ij = 2 * b_ij`  
`c) 12 month hold -> We define b'_ij = 4 * b_ij`  

`Payout_hold_ij = b'_ij / sum(b'_kl for all apps k in A and active holds l)`  
`Payout_hold_i = sum(b'_ij for all holds j for app i)`

**Option 2 - Continuous**  
The continuous option would pay a proportional payment to each developer wallet based on the amount of Kin they hold (minimum balance) each day. 

The notation for the holding payout calculation is as follows (computed daily, paid out monthly):  
`Let w_i = min(KRE_prior_payouts_i, minimum amount of Kin in KRE wallet during a day)`  
`Payout_hold_i = min(w_i / sum(w_j for all apps j in A) * KRE_hold, w_i * 50% / 365)`  

Note that we have capped developers to receive a holding reward no greater than 50% of the size of their KRE wallet holdings divided by 365 days in a year. Also note that a developer's `KRE wallet` will include both their KRE payout wallet and an optional verified cold-storage wallet they have provided.

The continuous option is less predictive than the fixed-term option because, unlike the fixed-term option, no Kin is explicitly locked up, so a developer can still sell at any point. The benefit of the fixed-term option to the ecosystem is the increased predictability of potential sell-pressure, the tradeoff is the higher friction point for developers who need to explicitly opt-in to the holding option by sending to an observable address. Note: In the current proposed implementation a developer could still opt out of a fixed-term hold since it is not locked in a smart contract, but they would lose the reward. There is implicit lock-in through this incentive. 

Given these tradeoffs, it is recommended that the continuous option is adopted, making this accessible for all developers with low technical complexity. 

**Final Payout**  
Across these three KRE tracks, a developers total payout would be:  
`Payout_i = Payout_spend_i + Payout_hold_i + Payout_buy_i`

## Implementation  
It is recommended that these new incentive structures take effect beginning January 1, 2020. In order to help developers in the economy get ramped up on the new incentive structure, we recommend a roll-out strategy of total KRE payout allocation as follows. We have presented two options:

**Option 1**

Month | Spend | Buy | Hold
------|-----|------------|---------
January | 90% | 5% | 5%
February | 80% | 15% | 5%
March | 70% | 20% | 10%
April | 60% | 30% | 10%
May | 50% | 40% | 10%
June | 40% | 45% | 15%
July | 30% | 55% | 15%
August | 20% | 65% | 15%
September | 10% | 75% | 15%

**Option 2**

Month | Spend | Buy | Hold
------|-----|------------|---------
January | 95% | 0% | 5%
February | 92% | 3% | 5%
March | 84% | 6% | 10%
April | 80% | 10% | 10%
May | 75% | 15% | 10%
June | 65% | 20% | 15%
July | 60% | 25% | 15%
August | 55% | 30% | 15%
September | 50% | 35% | 15%
October | 45% | 40% | 15%
November | 40% | 45% | 15%
December | 35% | 50% | 15%

The more aggressive Option 1 will force developers to move quickly and generate buy demand as fast as possible. Developers who succeed will be rewarded very heavily for doing so, but those who cannot adjust quickly will see their payouts diminish. While Option 2 generates buy demand more slowly, it is likely the safer (and our recommended option) to allow developers to adjust more gradually as the KRE changes focus.

`KRE_total`: The total amount is still to be defined. A budget will be presented to the Kin Foundation Board at a later time. For 2019 this is `590,000,000` Kin per day.

The notation for KRE payout allocation will be as follows (sample month: January, Option 2):  
`KRE_das = 0.95 * KRE_total`
`KRE_buy = 0.00 * KRE_total`
`KRE_hold = 0.05 * KRE_total`

**The KRE Carryover Pool**  
Like in the KRE 1.0, Kin that was not paid out to developers will accumulate for future use. We propose rebranding this to be the “carryover pool” as opposed to the “bonus pool” to more clearly articulate its purpose. 

Given the constraints proposed in the KRE tracks above, there may be unused payout on any given day. If there is unused payout for a particular KRE track this will become carryover pool added to future payouts averaged over the remainder of the year.

The notation for the KRE carryover pool calculation is as follows:  

Let `r` be the number of days left in 2020
Let `KRE_carryover` be the KRE carryover pool (initialized at 0)

Before a payout:
```
If KRE_carryover > 0:
    KRE'_total = KRE_total + [KRE_carryover / r]
    Apps will be paid based on KRE'_total
```

After a payout:
```
If sum(Payout_x_i for all apps i in A) < KRE_total:
    KRE_carryover += sum(Payout_i for all apps i in A)
```

**Monopoly Clause** 

As in KRE 1.1 we propose a continuation of the Monopoly Clause. The fundamental change is that it will apply separately to each KRE track to ensure that developers targeting a specific track will still be able to compete effectively.

Let `s_1, s_2, …, s_n` be the KRE payout shares for a specific track ordered by payout proportion in descending order before invoking the monopoly clause.
```
If (s_1 + s_2  > 0.90) or (s_1 > 0.5):
    If s_1 > 0.5:
        s_1' = 0.5 + ((s_1 - 0.5) / 0.5) * (2/3 - 1/2)
    Else:
        s_1' = s_1
    If s_1' + s_2  > 0.90 then:
        s_2 = s_2 / (s_1 + s_2) * 0.9

    s_1’ = minimum(s_1 / (s_1 + s_2) * 0.9, s_1')
    If s_1’ == s_1 / (s_1 + s_2) * 0.9:
        For i = 3 to n:
            s_i’ = s_i / (sum from i = 3 to n of s_i) * 0.1
    Else:
        For i = 2 to n:
            s_i’ = s_i / (sum from i = 2 to n of s_i) * (1 - s_1')
	Developers are paid out based on s_i’
Else:
	Developers are paid out based on s_i
 ```

For a more complete explanation of the reasoning behind the Monopoly Clause and examples please refer to [KRE V1.1](kik_kre_1_1.md).
