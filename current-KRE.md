# Kin Rewards Engine 

The purpose of this document is to provide an overview of the methodology and rules used for the Kin Rewards Engine.

## KRE 1.1
KRE 1.1 will continue to run until until December 31, 2019. Starting January 1, 2020, payouts will be based on KRE 2.0 which is described below.

## Base Algorithm
```
Let DAS_i be the number of daily active spenders in app i.
Let DAS_p2p_i be the number of peer to peer spenders in app i.
Let KSR be the $ to kin conversion rate (based on the 7 day weighted average from CoinMarketCap)
```
We define the daily payout for app i as:
```
DP_i = DAS_i * $0.09 + DAS_p2p_i * $0.01 * KSR
```
And the total daily payout (DP) will be:
```
DP = sum(DP_i for all apps i)
```
Daily Reward Budget
Daily Reward Budget (DRB) is the amount of Kin available for distribution to developers each day. This amount is equivalent to 590,000,000 kin per day for the remainder of 2019


## KRE Pool
In the event that the daily payout is less than the daily reward budget, the difference will be added to the KRE Pool (KRE_pool). This pool will be used to increase the amount of Kin in the daily reward budget for developers
```
KRE_pool += DRB - DP
```
Additional Daily Reward
In the event the Daily Payout is greater than the Daily Reward Budget, the KRE Pool can be used to add an Additional Daily Reward (ADR). This will be calculated by dividing the KRE pool by the number of days remaining in that given year. 
```
ADR = KRE_pool / # of days remaining in the year
```
Proportionate Spend 
If the amount that is to be paid via the Daily Payout is greater than the Daily Reward Budget plus the Additional Daily Reward, the developer will receive a percentage of the payout based on their DAS relative to the total DAS. 
```
If DP > DRB + ADR then:
	DP’_i = [DP_i / sum(DP_j for all apps j)] * (DRB + ADR)
	Apps are paid out based on DP’_i
Else:
	Apps are paid out based on DP_i
```
## Monopoly Clause
No single developer will receive more than 66.67% of the KRE payout for a given period and any developer that would have received more than 50% of the payout will have their payout adjusted.
No two developers will receive more than 90% of the KRE payout for a given period.
In both cases, residual payouts will be redistributed proportionally to other developers

Let `s_1, s_2, …, s_n` be the KRE payout shares ordered by payout proportion in descending order before invoking the monopoly clause.
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
	Developers are paid out based on s_i’
Else:
	Developers are paid out based on s_i
 ```

**Example 1:**  
Payout shares before clause: `{0.35, 0.3, 0.2, 0.15}`  
Payout shares after clause: `{0.35, 0.3, 0.2, 0.15}`  
Reasoning: Clause does not apply

**Example 2:**  
Payout shares before clause: `{0.90, 0.05, 0.03, 0.02}`  
Payout shares after clause: `{0.633, 0.183, 0.11, 0.073}`  
Reasoning: 2.i.1 applies

**Example 3:**  
Payout shares before clause: `{0.50, 0.45, 0.03, 0.02}`  
Payout shares after clause: `{0.474, 0.426, 0.06, 0.04}`  
Reasoning: 2.i.2 applies

**Example 4:**  
Payout shares before clause: `{0.55, 0.44, 0.01}`  
Payout shares after clause: `{0.486, 0.414, 0.06, 0.10}`  
Reasoning: Both 3.1 and 3.2 apply, first `0.55` is changed to `0.517` by 3.1, then `0.517` and `0.44` are changed to by 2.a.2.

While `66.67%` seems high for a single developer to receive, we do not want to discourage strong developers from entering the ecosystem. Moreover, because any app with payout shares above `50%` will be adjusted, most of the time the top app will receive much less than `66.67%`:


Payout shares before clause | Payout shares after clause
--------------------------- | --------------------------
`50%` | `50%`
`60%` | `53.33%`
`70%` | `56.67%`
`80%` | `60%`
`90%` | `63.33%`
`95%` | `65%`

This table assumes that 2.i.2 does not apply.

## KRE 2.0 

**Payout**  
Across the three KRE tracks (Spend, Buy, Hold), a developer's (developer `i`) total payout would be:  
`Payout_i = Payout_spend_i + Payout_buy_i + Payout_hold_i`

## 1. Spend  
`Let KRE_spend be the total amount of Kin paid to developers for the Spend track in a day.`  
`Let spend_i be the number of users who spend Kin in a day in app i.`  
`Payout_spend_i = min(KRE_spend * spend_i / sum for all apps i (spend_i), 15000 * spend_i)`  

Starting Feb 1, 2020 the payout proportions will be: 

Kin spent per DAS per day | 1 - 9 Kin spent per day | 10 - 99 Kin spent per day | 100 - 999 Kin spent per day | 1,000+
--------------------------|-------------------------|---------------------------|-------------------------|-------
Max Payout per spender | 3,000 Kin | 6,000 Kin | 12,000 Kin | 30,000 Kin

Thresholds and maximum payout amounts will be recalibrated on a quarterly basis to align with roughly $0.15 for a 1,000+ Kin spender (assuming the price of Kin is still below $0.15 for 1000 Kin). In the event of a dramatic price change (+/- 50% as defined by a 7-day average of closing price on CoinMarketCap), this frequency of recalibration can be more dynamic and can be addressed through a proposal to the Foundation.

The notation of the Spend algorithm going forward will then be:  
`Let KRE_spend be the total amount of Kin paid to developers for the Spend track in a day.`  
`Let spend_i_1 be the number of users who spend 1-9 Kin in a day in app i.`  
`Let spend_i_10 be the number of users who spend 10-99 Kin in a day in app i.`  
`Let spend_i_100 be the number of users who spend 100-999 Kin in a day in app i.`  
`Let spend_i_1000 be the number of users who spend 1000 or Kin in a day in app i.`  
`Then spend_i = spend_i_1 + 2*spend_i_10 + 4*spend_i_100 + 10*spend_i_1000`  
`Payout_spend_i = min(KRE_spend * spend_i / sum for all apps i (spend_i), 3000 * spend_i)`  

## 2. Buy
`Let KRE_buy be the total amount of Kin paid to developers for the Buy track in a day`<br/>
`Let w_increase_i be the summed user wallet balance increase in app i over the lifetime of the KRE`  <br/>
`Let w_decrease_i be the summed wallet balance decrease in app i over the lifetime of the KRE`  <br/>
`w_i is the amount of Kin held in a developer's holding wallet from prior KRE payouts. This is properly defined in the Holding section`<br/> 
`Let KRE_prior_buy_demand_payouts_i be the summed Kin paid to app i over the lifetime of the KRE (including grants)`<br/>  

We define `buy_demand_i` for app `i` as:  
`buy_demand_i = max(w_increase_i - w_decrease_i - KRE_prior_buy_demand_payouts_i + minimum(w_i, KRE_prior_buy_demand_payouts_i), 0)`

Then the buy payout for app i is:  
`Payout_buy_i = min(KRE_buy * buy_demand_i / (sum for all apps j buy_demand_j), buy_demand_i)`

## 3. Hold
The notation for the holding payout calculation is as follows:  
`Let w_i = min(KRE_prior_payouts_i, minimum amount of Kin in KRE wallet during a day)`  
`Payout_hold_i = min(w_i / sum(w_j for all apps j in A) * KRE_hold, w_i * 50% / 365)`  
Note that a developer's KRE wallet will include both their KRE payout wallet and an optional verified cold-storage wallet they have provided.

## Implementation

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

`KRE_total`: This will be 500,000,000 Kin / day in 2020.

The notation for KRE payout allocation will be as follows (sample month: January, Option 2):  
`KRE_das = 0.95 * KRE_total`

`KRE_buy = 0.00 * KRE_total`

`KRE_hold = 0.05 * KRE_total`

**The KRE Carryover Pool**  
Like in the KRE 1.0, Kin that was not paid out to developers will accumulate for future use. If there is unused payout for a particular KRE track this will become carryover pool added to future payouts averaged over the remainder of the year.

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

For a more complete explanation of the reasoning behind the Monopoly Clause and examples please refer to to the Monopoly Clause section above.
