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
- That Kin was purchased in exchange for fiat currency
- That the user received Kin in exchange for this purchase taking place
- Which digital service (app) the purchase was made through
- Which submitted Buy Track module was used

Specifically, for each user earn counted through the module, a buy_id must be appended to the memo field of all earn transactions done through the module. A buy_id is of the form *-mod_id-ref_id* where:
- *mod_id* is a 4-digit module identifier for the Buy Track module (i.e. *kads*)
- *ref_id* is a unique reference id created by the module developer which exists in another Kin blockchain transaction (we will refer to this as the reference_txn).

In total, the earn transaction memo field would be of the form:
- *1-app_id-mod_id-ref_id* i.e. *1-lipz-kads-abcdefg01*

The transaction ref_id is a 10-digit alphanumeric identifier that must exist in the memo field of  the reference_txn. The refernce_txn must be formatted as follows:
- *1-mod_id-ref_id* i.e. *1-kads-abcdefg01*

The reference_txn would be either:
- The actual transaction where the Kin purchase in exchange for fiat currency took place
- A record-keeping payment transaction with amount 0.01 Kin sent to a module-specific address (can be any wallet created by the developer). This may be done in cases where fiat currency-exchange transactions are batched over a time period. In addition, the Buy Track module submission must contain information into how this information can be audited by KRE Operators or other parties. It must be verifiable that the same amount of Kin that was claimed to be purchased through the module was in fact sent to users and/or developers.

Developers must submit this form (google form link TODO) which must be approved by the Kin Foundation prior to counting towards the KRE.

## Implementation
Because this is a large change we propose this goes into effect no earlier than 45 days after the Kin Foundation has accepted the proposal which will give ample time for community development.
