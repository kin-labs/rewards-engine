# Kin Rewards Engine 

The purpose of this document is to provide an overview of the methodology and rules used for the Kin Rewards Engine.

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
        s_2 = s_2 / (s_1+s_2) * 0.9

    s_1’ = minimum(s_1 / (s_1+s_2) * 0.9, s_1')
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

**Example 1:**  
Payout shares before clause: `{0.35, 0.3, 0.2, 0.15}`  
Payout shares after clause: `{0.35, 0.3, 0.2, 0.15}`  
Reasoning: Clause does not apply

**Example 2:**  
Payout shares before clause: `{0.90, 0.05, 0.03, 0.02}`  
Payout shares after clause: `{0.663, 0.183, 0.11, 0.073}`  
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
