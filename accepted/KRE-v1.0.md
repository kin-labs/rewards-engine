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
