# Kin Improvement Proposal - KRE V1.1
The purpose of this document is to outline a proposed improvement to the existing KRE V1 algorithm. 

## Proposed by: Kik Interactive Inc. 

## Abstract
The objective of [KRE V1.0](https://github.com/kinecosystem/rewards-engine/blob/master/accepted/KRE-v1.0.md) was to incentivize developers to get people using Kin. Within that parameter, the current iteration of the KRE has been successful. As of this writing November 19th, 2019 there are over 1 million monthly active spenders across 83 independent apps. However, while the ecosystem continues to grow, there have been some vulnerabilities exposed in the current algorithm that we aim to address in this improvement proposal. This KRE V1.1 proposal is being put forth for immediate adoption. We have also submitted a proposal for a [KRE V2.0](kik_kre_2_0.md) to commence January 2020.

## Summary of Improvements
The following improvement proposal consists of three elements (two spend guideline changes and one change to the KRE algorithm itself): 
1. Valid Spend Guidelines Updates
   1. Update to the subscription guidelines
   1. Transparency Clause
1. KRE Algorithm Update
   1. Monopoly Clause

## 1. Valid Spend Guidelines Updates

**i. Subscription Guidelines**

In the current guidelines passive payments are not included in the definition of a Daily Active Spender except for a subscription. The current subscription guidelines allow a user to opt into daily payments where their wallet passively pays Kin in the background. Going forward, we are proposing that subscriptions are limited to a monthly cadence. The day in which this payment comes through will count as a daily active spender, but any passive payments that occur within the month will not count. 

Monthly was selected based on the industry standard for subscription based services ie. Netflix, Spotify, Audible. Weekly and bi-weekly passive payments were also considered, however, in our view this cadence is inconsistent with standard expectations of user experience for subscriptions and would therefore only be implemented to gain additional KRE payments in the current DAS payout framework. The proposed [KRE V2.0](https://github.com/kinecosystem/kin-rfcs/improvment-proposals/kik_kre_1_1.md) aims to address this and make the frequency of payments irrelevant through a proportional payout structure tied to the value of the transaction. 

**ii. Transparency Clause**

There are currently no guidelines on transparency of applications participating in the KRE. The KRE is an open incentive protocol. To ensure fairness in the KRE we are proposing a transparency clause where only apps that are public known entities are eligible for KRE payouts. This benefits the ecosystem broadly by increasing discoverability of each of the apps and will also allow the community to hold each app accountable for adherence to the guidelines.

## 2. KRE Algorithm Update

**i. Monopoly Clause**

The purpose of the KRE is to drive the growth of a healthy economy. The foundation of a thriving economy is healthy competition. Absent competition, innovation slows and consumer experience diluted. Given that, we are recommending a monopoly clause to the KRE that would stop any developer from monopolizing the KRE payout. This will ensure there is an opportunity for other developers to contribute and be fairly compensated. The monopoly clause has been modelled on existing precedent from antitrust legislation in place to promote healthy competition. There are two prongs to the proposed monopoly clause: 
No single developer will receive more than 66.67% of the KRE payout for a given period and any developer that would have received more than 50% of the payout will have their payout adjusted.
No two developers will receive more than 90% of the KRE payout for a given period.
In both cases, residual payouts will be redistributed proportionally to other developers

Let `s_1, s_2, …, s_n` be the KRE payout shares ordered by payout proportion in descending order before invoking the monopoly clause.
```If s_1 + s_2  > 0.90 or s_1 > 0.5:
If s_1 > 0.5:
	s_1 = 0.5 + ((s_1 - 0.5) / 0.5)*(2/3 - 1/2)
	If s_1 + s_2  > 0.90 then:
		s_2 = s_2 / (s_1+s_2) * 0.9

	s_1’ = minimum(s_1 / (s_1+s_2) * 0.9, )
	If s_1’ = s_1 / (s_1 + s_2) * 0.9:
		For i = 3 to n:
			s_i’ = s_i / (sum from i = 3 to n of s_i) * 0.1
	Else:
		For i = 2 to n:
			s_i’ = s_i / (sum from i = 2 to n of s_i) * (1 - s_i)
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

We also considered a variety of other approaches but arrived on this approach because it appeared to be the simplest and least restrictive rule that could be placed while still stopping 1 or 2 very large developers from taking over the entire KRE. The current recommendation still allows 3 large players to take most of the KRE reward. 

Alternatively, we looked at using the Herfindahl–Hirschman Index which is used to measure the amount of competitiveness in an industry. More specifically, it is the sum of the squares of market shares (KRE payouts in our case) of firms in an industry:
I.e. `Shares = {50%, 25%, 10%} -> Herfindahl Index = 0.5^2 + 0.25^2 + 0.1^2 = 0.3225`
The higher this value, the more concentrated the market is. We examined ways to redistribute KRE payouts based on a Herfindahl Index limit, but felt the math was too complicated to warrant its use. Specifically, deciding which developers would have their payouts increased or decreased and by how much based on their contribution to the Herfindahl Index was quite complex.

## Implementation
It is recommended that this proposal be adopted for the next KRE cycle beginning November 24th, 2019. To ensure consistency with the guidelines, payout details and calculations will be published alongside the output.
