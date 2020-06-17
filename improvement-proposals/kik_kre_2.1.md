# Kin Improvement Proposal
The purpose of this document is to outline a proposed improvement to the existing KRE algorithm. 

*versioning:*
- *2.1*

## Proposed by:
*Kik Interactive Inc*

## Abstract
This is two fixes to clean up the Buy Track. First, we propose simple fix to remove the language "buy demand" and replace with "net demand". While the Buy Track definitely does incentivize developers to create buy demand for users, the variable "buy_demand_i" is not actually an accurate description of buy demand. In order to alleviate confusion, we recommend replacing this language with "net demand". 

Second, we propose to remove the *minimum(w_i, KRE_prior_buy_demand_payouts_i)* terms from the demand calculation. This was an oversight in the original proposal and the current implementation will award developers repeatedly for the same demand generation (assuming they hold their buy payouts).

## Summary of Improvements
- Replace all references to "buy_demand_i" with "net_demand_i" and all references to "KRE_prior_buy_demand_payouts_i" with "KRE_prior_buy_payouts_i".
- Remove *minimum(w_i, KRE_prior_buy_demand_payouts_i)* from the (now) "demand_i" equation. 

Specifically: <br/>
We define `buy_demand_i` for app `i` as: <br/>
`buy_demand_i = max(w_increase_i - w_decrease_i - KRE_prior_buy_demand_payouts_i + minimum(w_i, KRE_prior_buy_demand_payouts_i), 0)`

Will be replaced with: <br/>
`Let demand_i be the amount of Kin that has flowed into user wallets: w_increase_i - w_decrease_i.`<br/>
Then we define net_demand_i for app i as:<br/>
`net_demand_i = max(demand_i - KRE_prior_buy_demand_payouts_i, 0)`

The reasoning behind this can be explained by the following example: Suppose a developer built a new app and had users earn 1000 Kin and then spend 500 Kin on the first day of the app. Both the old and new equation would show the developer had 500 *net demand* and would be paid up to 500 Kin (based on the demand of other apps). For simplicity, assume the developer was paid the full 500 Kin. Now, because *w_increase_i* and *w_decrease_i* are calculated over the lifetime of the application, if the developer never had any more user activity these would remain at 1000 and 500 respectively. In the old equation, if the developer held all of their KRE payouts, they would be paid 500 every day (forever) for their original contribution which is not in line with the intention of the Buy Track of the KRE.

## Implementation
We propose that this change happens immediately pending approval from the Kin Foundation.
