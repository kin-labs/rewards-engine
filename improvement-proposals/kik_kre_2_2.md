# Kin Improvement Proposal
The purpose of this document is to outline a proposed improvement to the existing KRE algorithm. 

*versioning:*
- *2.2*

## Proposed by:
*Kik Interactive Inc*

## Abstract
We believe that for the Kin economy to continue to grow, the ecosystem needs to focus on driving real demand for Kin. In order to more directly drive this goal we recommend 2 changes:
- Update the Buy Track to pay developers more directly by measuring buy demand through whitelisted gateways (i.e. advertising module, buy module).
- Update the Carryover Pool to move to 3 discrete Carryover Pools (one for each track) which will create a stronger incentive for developers to adjust to the Buy Track.

## Summary of Improvements
The initial vision for the Buy Track in KRE 2.0 incentivizes developers to get users to buy kin while making sure that it produces more buy pressure than sell pressure on the market with as few restrictions as possible: developers can get users to earn Kin however they see fit. While this formulation of the Buy Track accomplished this, the Buy Track (in conjuction with the rest of the KRE) has a few problems:
- Developers have shared that it is hard to optimize for the Buy Track because the logic is complex and less direct
- While the buy/sell pressure created from the Buy Track may be neutral, it does not directly incentize developers to get users to buy kin

In order to address these problems, our proposed improvement has 2 parts:
### 1. Buy Track Update
In order for developers to be more strongly incentivized to get users to buy Kin, we wish to simplify the Buy track to reward developers more directly for purchases of Kin by users in dollars or attention. The existing logic of the buy track would be replaced with the following:<br/>

`Let KRE_buy be the total amount of Kin paid to developers for the Buy track in a day`<br/>
`Let buy_i be the total amount of Kin purchased and sent to users through their attention (ads) or fiat currency through a registered whitelisted module in app i in a day.`  <br/>

Then the buy payout for app i is:  
`Payout_buy_i = min(KRE_buy * buy_i / (sum for all apps j buy_j), buy_i)`

In order for new modules to be added to the set of existing whitelisted modules, developers will have to submit new modules to the Kin Foundation (see Module Submission). New modules will need to demonstrate that Kin is being purchased and sent to a user through some means. On launch, the first whitelisted module of the Buy Track will be Kin Ads.

### 2. Carryover Pool Update
In order to push developers to adapt to the updated Buy Track, we recommend the KRE Carryover Pool be split into 3 distinct pools: one per track. This will ensure that unused payouts from the Buy Track will not flow back into the Spend Track pushing developers more strongly to adapt. 

On the first day this proposal becomes takes effect the current KRE Carryover Pool will be split into 3 (based on that month's KRE payout proportion). For example, suppose that first day is August 1, 2020:
Let `KRE_carryover_spend` = `KRE_carryover` * 0.5
Let `KRE_carryover_hold` = `KRE_carryover` * 0.15
Let `KRE_carryover_buy` = `KRE_carryover` * 0.35

The existing logic of the KRE Carryover Pool would be replaced with the following: <br/>

Let `r` be the number of days left in 2020
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

### Module Submission

In order for a submitted module to be recognized for use in the Buy Track it must be demonstrated that user actions resulted in the purchase of Kin. Blockchain transactions must occur for each user earn that happens through the module demonstrating:
- That the user received Kin in exchange for a Kin purchase taking place
- Which digital service (app) the purchase was made through
- Which submitted Buy Track module was used

Specifically, for each user earn counted through the module, a *mod_id* must be appended to the memo field. A *mod_id* is a 4-digit module identifier for the Buy Track module (i.e. *kads*)

In total, the earn transaction memo field would start with the form:
- *1-app_id-mod_id* i.e. *1-lipz-kads*

In addition, payment transactions from modules to developers must start with the form:
- *1-mod_id*

In addition, the Buy Track module submission must contain additional information as to how it can be audited by KRE Operators or other parties. In addition to the above, developers must fill out this [form](https://docs.google.com/forms/d/e/1FAIpQLSf5h20erxuLMTFIWwqQxLynLyQV-UYXXMgOaamRArPxzL9afQ/viewform?usp=sf_link) which must be approved by the Kin Foundation prior to counting towards the KRE. In order for the submission to approved:
- It must be verifiable that the amount of Kin claimed to be sent to users through the module is no more than the amount of Kin sent to the developer from the module creator.
- The user either watched an advertisement, filled out a survey or paid in another currency for the Kin before Kin was sent to the user.
- The user is paid Kin at a rate at most 3x the market rate (i.e. a user can earn at most $0.03 worth of Kin for an ad generating $0.01 of revenue, and a user buying $1.00 worth of kin cannot receive more than $3.00 worth of Kin).

We think this is the best path forward for data collection, but we considered two other options. First, we considered also requiring a 10-digit *ref_id* in the memo field of earn transactions we as well as individual Kin purchase (or empty accounting transactions) which would have made it possible to audit every purchase transaction. This would be very cumbersome though for module developers and module users to implement so we decided against it. We also considered removing the *mod-id* completely which would have made it incredibly easily to implement for all parties. However, without *mod-id* in transactions, we would have no way as a ecosystem to know how many daily active buyers (and other key buying metrics) we have.

## Implementation
Because this is a large change we propose this goes into effect no earlier than 45 days after the Kin Foundation has accepted the proposal which will give ample time for community development.
