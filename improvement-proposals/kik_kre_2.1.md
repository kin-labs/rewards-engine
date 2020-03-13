# Kin Improvement Proposal
The purpose of this document is to outline a proposed improvement to the existing KRE algorithm. 

*versioning:*
- *2.1*

## Proposed by:
*Kik Interactive Inc*

## Abstract
This is two fixes to clean up the Buy Track. First, we propose simple fix to remove the language "buy demand" and replace with simply "demand". While the Buy Track definitely does incentivize developers to create buy demand for users, the variable "buy_demand_i" is not actually an accurate description of buy demand. In order to alleviate confusion, we recommend replacing this language with "demand". Second, we propose to remove the *minimum(w_i, KRE_prior_buy_demand_payouts_i)* terms from the demand calculation. This was an oversight in the original proposal and the current implementation will award developers repeatedly for the same demand generation (assuming they hold their buy payouts).

## Summary of Improvements
- Replace all references to "buy_demand_i" with "demand_i" and all references to "KRE_prior_buy_demand_payouts_i" with "KRE_prior_buy_payouts_i".
- Remove *minimum(w_i, KRE_prior_buy_demand_payouts_i)* from the (now) "demand_i" equation.

## Implementation
We propose that this change happens immediately pending approval from the Kin Foundation.
