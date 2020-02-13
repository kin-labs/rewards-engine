# Kin Rewards Engine 

The purpose of this document is to provide an overview of the methodology and rules used for the Kin Rewards Engine.

## KRE 2.0 

**Payout**  
Across the three KRE tracks (Spend, Buy, Hold), a developer's (developer `i`) total payout would be:  
`Payout_i = Payout_spend_i + Payout_buy_i + Payout_hold_i`

Note that a developer will only be rewarded KRE payouts for days where at least one Kin blockchain transaction took place in their respective application.

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

The notation for KRE payout allocation will be as follows (sample month: January, Option 2):  <br/>
`KRE_das = 0.95 * KRE_total`<br/>
`KRE_buy = 0.00 * KRE_total`<br/>
`KRE_hold = 0.05 * KRE_total`<br/>

**The KRE Carryover Pool**  
Like in the KRE 1.0, Kin that was not paid out to developers will accumulate for future use. If there is unused payout for a particular KRE track this will become carryover pool added to future payouts averaged over the remainder of the year.

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

As in KRE 1.1 we propose a continuation of the Monopoly Clause. The fundamental change is that it will apply separately to each KRE track to ensure that developers targeting a specific track will still be able to compete effectively.

No single developer will receive more than 66.67% of the KRE payout for specific track for a given period and any developer that would have received more than 50% of the track's payout will have their track payout adjusted.
No two developers will receive more than 90% of any KRE track's payout for a given period.
In both cases, residual payouts will be redistributed proportionally to other developers

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
	Developers are paid out based on s_i’
Else:
	Developers are paid out based on s_i
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

While `66.67%` seems high for a single developer to receive, we do not want to discourage strong developers from entering the ecosystem. Moreover, because any app with payout shares above `50%` will be adjusted, most of the time the top app will receive much less than `66.67%`:


Payout track shares before clause | Payout track shares after clause
--------------------------- | --------------------------
`50%` | `50%`
`60%` | `53.33%`
`70%` | `56.67%`
`80%` | `60%`
`90%` | `63.33%`
`95%` | `65%`

This table assumes that 2.i.2 does not apply.
