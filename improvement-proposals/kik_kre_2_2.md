# Kin Improvement Proposal
The purpose of this document is to outline a proposed improvement to the existing KRE algorithm. 

*versioning:*
- *2.2*

## Proposed by:
*Kik Interactive Inc*

## Abstract
We believe that for the Kin economy to continue to grow, the ecosystem needs to focus on driving real demand for Kin. In order to more directly drive this goal we recommend 3 changes:
- Update the Buy Track to reward developers directly for users purchasing Kin with their attention or fiat currency via whitelisted modules.
- Update the Carryover Pool to become 3 different Carryover Pools (one for each track) which will further force developers to adjust to the Buy Track.
- Update the Spend Track to pay developers for higher spend users; creating stronger incentive for users to earn and spend large amounts of Kin.

## Summary of Improvements
The initial vision for the Buy Track in KRE 2.0 was incentivizing developers to get users to buy kin while making sure that it produced more buy pressure than sell pressure on the market. While the current formulation of the Buy Track accomplishes this, the Buy Track (in conjuction with the rest of the KRE) has a few problems:
- Developers are stating that the Buy Track is too complicated to properly optimize for
- While the buy/sell pressure created from the Buy Track may be neutral, it does not directly incentize developers to get users to buy kin
- Developers are not incentivized to get users to spend more than 1000 Kin at a time (less than a penny USD at the time of writing). This leads to use cases where experiences cost exactly 1000 Kin in app, and users will have very little incentive to trade any meaningful amount of fiat for Kin.

In order to address these problems, our proposed improvement has 3 parts:
### 1. Buy Track Update
In order for developers to be more strongly incentivized to get users to buy Kin, we wish to simplify the Buy track to reward developers more directly for purchases of Kin by users in dollars or attention. The existing logic of the buy track would be replaced with the following:<br/>

`Let KRE_buy be the total amount of Kin paid to developers for the Buy track in a day`<br/>
`Let buy_i be the total amount of Kin purchased and sent to users through their attention (ads) or fiat currency through a registered whitelisted module in app i in a day.`  <br/>

Then the buy payout for app i is:  
`Payout_buy_i = min(KRE_buy * buy_i / (sum for all apps j buy_j), buy_i)`

In order for new modules to be added to the set of existing whitelisted modules, developers will have to submit new modules to the Kin Foundation (process TBD). New modules will need to demonstrate that Kin is being purchased and sent to a user through some means. On launch, the first whitelisted module of the Buy Track will be Kin Ads.

### 2. Carryover Pool Update
In order to push developers to adapt to the updated Buy Track, we recommend the KRE Carryover Pool be split into 3 distinct pools: one per track. This will ensure that unused payouts from the Buy Track will not flow back into the Spend Track pushing developers more strongly to adapt. The existing logic of the KRE Carryover Pool would be replaced with the following: <br/>

Let `r` be the number of days left in 2020
On June 1, 2020 (or the first day this proposal becomes takes effect) the current KRE Carryover Pool will be split into 3 (based roughly on average payouts for the remainder of 2020):
Let `KRE_carryover_spend` = `KRE_carryover` * 0.5
Let `KRE_carryover_hold` = `KRE_carryover` * 0.15
Let `KRE_carryover_buy` = `KRE_carryover` * 0.35

Before a payout:
```
If KRE_carryover_spend > 0:
    KRE_spend += [KRE_carryover_spend / r]
If KRE_carryover_hold > 0:
    KRE_hold += [KRE_carryover_hold / r]
If KRE_carryover_buy > 0:
    KRE_buy += [KRE_carryover_buy / r]
```

After a payout:
```
If sum(Payout_spend_i for all apps i in A) < KRE_spend:
    KRE_carryover_spend += KRE_spend - sum(Payout_spend_i for all apps i in A)
If sum(Payout_hold_i for all apps i in A) < KRE_hold:
    KRE_carryover_hold += KRE_spend - sum(Payout_hold_i for all apps i in A)
If sum(Payout_buy_i for all apps i in A) < KRE_buy:
    KRE_carryover_buy += KRE_spend - sum(Payout_buy_i for all apps i in A)
```

### 3. Spend Track Update
In order to further drive the incentives for developers to get users to want large amounts of Kin we are proposing increased rewards for developers for users spending large amounts of Kin.
We give two potential options for this task. The first simply adds several new buckets for the spend track while the other gives a function which will calculate the value of each individual daily spender.
1. We update the Spend Track buckets to be as follows:
  
Kin spent per DAS per day | 1 - 9 | 10 - 99 | 100 - 999 | 1,000 - 9,999 | 10,000 - 99,999 | 100,000 - 999,999 | 1,000,000+
--------------------------|-------|---------|-----------|---------------|-----------------|-------------------|-----------
Max Payout per spender | 3,000 Kin | 6,000 Kin | 12,000 Kin | 30,000 Kin | 75,000 Kin | 225,000 Kin | 750,000 Kin

2. We replace the existing logic in the Spend Track with the following:
 
`Let KRE_spend be the total amount of Kin paid to developers for the Spend track in a day.` <br/>
`Let spend_i_j be the amount of Kin user j spent in app i in a day.` <br/>
`Let spend_units_i = sum for all users j in app i (spend_i_j^(log(2)))` <br/>
`Payout_spend_i = KRE_spend * spend_units_i / sum for all apps j (spend_units_j)`

This effectively means a few things. Firstly, the entire Spend Track payout will be spent each day (this would have almost certainly happened anyway). Secondly, a user who spends 10 Kin will be worth twice as much as a user who spends 1 Kin, 100 Kin spender 4 times as much as a 1 Kin spender and so on. Most importantly though, a user who spends an arbitrary amount of Kin (say 8,000 Kin for the sake of argument) would be worth ~15 times as much as a user who spent 1 Kin, instead of being bucketed and worth the same as a 1,000 Kin Spender (only 8 times as much as a 1 Kin Spender using this formula). 

While it would be nice to have a simpler formula for calculating spenders, we think it is important for the formula to be sub-linear: as the amount of Kin spent goes up, the return for spending decreases. This ensures that, over a certain threshold the amount paid by the KRE for the spender is less than the amount spent by the spender. This limits the impact of a form of "Kin recycling" where developers give Kin to users to spend and are then paid back to the KRE more than what they gave to the users.

## Implementation
Because this is a large change we propose this goes into effect July 1, 2020 which will give ample time for community feedback and development.
