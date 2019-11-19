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
# Valid KRE Spend Guidelines
### Key concepts
1. The user has control over the initiation of a transaction
2. The user is aware that a transaction is happening
### Terminology
- Valid spend - A spend that follows the guidelines; will be rewarded by the KRE
- User - A human being (consumer/creator) with a single wallet in the app
- Spend - A transaction between a user and developer (in-app/U-to-D)
- P2P - A transaction between two or more users
- Subscription - An automated payout distributed over a set period of time, regardless of usage
- Profile - A generic name for a handle that represents a user
### Usability guidelines
A transaction must be initiated by a user action, while the Kin logo must be visible on a button.
### Peer-to-peer (P2P) transactions
1. Only 1 Kin can be spent per tap (ie. like/heart/K)
- A single tap must communicate clearly to the user that a payment was made
- Users must have the ability to acknowledge and dismiss these communications
- Once acknowledged, there is no need to re-communicate with the user
2. In transactions of more than 1 Kin, the amount must be clearly stated on or near the action/button
3. Transactions of more than 1 Kin require a flow with a minimum of 2 clicks (undo/confirm/user input
amount/amount selection)
### User-to-developer (U-to-D) transactions
4. Every U-to-D experience, regardless of the amount transacted, must include the following:
- Clear messaging communicating the transaction amount
- Clear messaging telling the user what they will receive in return for their Kin 
- Must be a confirm/acknowledge button
### Subscription guidelines
Subscriptions can be daily, weekly, monthly, or yearly.
Comment: A user can subscribe to an app (spend) or to a specific content creator (P2P)
5. Subscriptions must be initiated explicitly by the user
6. Transactions must be set to a fixed amount (from charge to charge)
7. Users must explicitly renew their subscription every X payments depending on the time period: Daily
(30), weekly (4), monthly (12), or yearly (1)
8. Before subscribing, the user must receive clear communication that includes:
- How much Kin will be charged in total
- Charging cadence and amount
- What the user receives as a subscriber
- A confirm/acknowledge button
- Information on how to unsubscribe
9. Users must be able to unsubscribe at any time
### Process handling for guidelines violation
If an app has an experience violating these guidelines:
1. App’s developer will be noticed about the violating experience
2. This app will be excluded from the KRE from the following payout
3. In order to be eligible again for KRE, there should be an updated app version in the App Store/Play
Store with the experienced fixed
