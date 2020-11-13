## Kin Improvement Proposal - KRE V3.0
The purpose of this document is to outline a proposed new version of the KRE Algorithm

## Proposed by: Kik Interactive Inc. 

## Abstract
The Kin Rewards Engine (KRE) is an algorithmic distribution of Kin to app developers driving growth of the Kin Economy. This is the primary mechanism that the Kin Foundation uses to allocate the Kin Reserves. [KRE 1.0](https://github.com/kinecosystem/rewards-engine/blob/master/accepted/KRE-v1.0.md) was introduced in February of 2019 and drove the number of active spenders in the economy. On January 1, 2020 [KRE 2.0](https://github.com/kinecosystem/rewards-engine/blob/master/accepted/KRE-v2.0.md) was introduced and aimed to slowly convert these spenders into buyers.
We propose KRE 3.0 to take effect Janurary 1, 2021. It aims to build upon learnings from KRE 1.0 and KRE 2.0 push our economy towards stability. It has two parts:
1. We recommend the daily payout cap be re-evaluated quarterly by the Kin Foundation. For Q1 2021, we recommend a daily payout cap of 250 million Kin or $USD 5000 in Kin, whichever is less.
1. We recommend the KRE payout logic be adjusted. We provide two options with the latter (ii) being our recommendation because of its simplicity.
   1. We improve upon the existing KRE payout structure with updates to the size of each track, a simplification of the Spend Track and tighter logic for the Buy Track.
   1. We simplify the KRE to one single track that rewards developers proportionally based on the sum of all Active User Balances in their app relative to the sum total of all Active User Balances across the Kin Ecosystem.

## Introduction

As mentioned, KRE 1.0 was introduced in February 2019 after the ecosystem had reached sufficient diversity and scale following the success of early developer programs. Given the economy was still in the early stages of growth, KRE 1.0 focused entirely on driving the number of active participants in the economy, defined as an “Active Spender”. KRE 1.0 was successful in driving this metric. By the end of 2019 the economy had grown to over 1 million Monthly Active Spenders (MAS). However, while the economy now had more people spending than any other cryptocurrency, the amounts were still small and most of these users were not driving meaningful demand for Kin on the open market. On January 1, 2020 KRE 2.0 was introduced which aimed to slowly convert these spenders into buyers. 

KRE 2.0 was split into 3 payment tracks:
1. The revised Spend Track incentivized developers to get users to spend more Kin.
1. The Buy Track incentivized developers to get their users to buy Kin. 
1. The Hold Track incentivized developers to hold their KRE payouts for longer

Through these three tracks, Kin Spent in apps has increased from roughly 5 million Kin / day in December of 2019 to over [350 million Kin / day](https://medium.com/kinblog/kin-economy-report-september-2020-b0685ad324e7) in September of 2020 and [almost 7 billion Kin](https://public.tableau.com/profile/kinfoundation#!/vizhome/KRE2_0NewDash/Dashboard1) has been purchased through approved modules since [KRE 2.2](https://github.com/kinecosystem/rewards-engine/blob/master/accepted/KRE-v2.2.md) took effect on August first. The holding behaviour from developers has remained relatively consistent since the introduction of the Hold Track. 
Despite this positive step forward, there are still challenges with the current KRE implementation. 
* The KRE does not discriminate between “high-quality” and “low-quality” spends which means that users who are programmatically earning and spending Kin with little understanding are rewarded the same as users who are intentionally buying and spending Kin.  
* Kin bought by users does not sufficiently offset the sell-pressure created by KRE payouts.
* The KRE payout logic is very complex.

In order to address these problems, the following proposal outlines a revision to both the daily KRE budget and the KRE logic. We provide two options for updating the KRE logic. Our recommendation is the latter option: Active User Balances.

## Daily Payout Cap
We recommend that the Kin Foundation re-evaluate and adjust daily payout caps on a quarterly basis to provide more flexibility when addressing changes in the economy. As the value on Kin has grown and the ecosystem has matured, the rate of inflation from KRE payouts will need to decrease in order to limit sell-side pressure from developers. This will enable the value of Kin to grow as adoption grows, which will increase participation and competition in the ecosystem.


We recommend that the daily payout is the lesser of either 250 million Kin or USD $5000 worth of Kin per day for Q1 of 2021*:

```
KRE_total = minimum(250000000, USD $5000 worth of Kin)
```

The daily price of Kin will be calculated as the average closing price on Coin Gecko of the 7 days immediately preceding the date in question.

\* *Because the price of Kin is still so volatile, we recommend that the Kin Foundation make their final decision about the Q1 payout cap at the Kin Foundation's December Board Meeting.*

## KRE Logic Update


### Option i: KRE 2.2.2 Extension
This option would be an incremental improvement to the existing KRE logic but with the reduced budget recommended above. The objective of this option is to improve the quality of spend and buy experiences for users. The challenge with this option is that it continues to be complex.

#### Track Schedule
Month | Spend | Buy | Hold
------|-----|------------|---------
January 2021 | 30% | 55% | 15%
February 2021 | 25% | 60% | 15%
March 2021 | 20% | 65% | 15%
April 2021 | 15% | 70% | 15%
May 2021 and onward | 10% | 75% | 15%

We recommend a continuation of the current trajectory where payments are shifted from the Spend Track to the Buy Track.

#### Spend Track

In order to simplify the Spend Track, we recommend that the caps on payout/spender are removed (these caps were and likely never will be reached). The specific logic remaining will be:

```
Let KRE_spend be the total amount of Kin paid to developers for the Spend track in a day.
Let spend_i_1 be the number of users who spend 1-9 Kin in a day in app i.
Let spend_i_10 be the number of users who spend 10-99 Kin in a day in app i.
Let spend_i_100 be the number of users who spend 100-999 Kin in a day in app i.  
Let spend_i_1000 be the number of users who spend 1000 or more Kin in a day in app i.
Then spend_i = spend_i_1 + 2*spend_i_10 + 4*spend_i_100 + 10*spend_i_1000
Payout_spend_i = KRE_spend * spend_i / sum for all apps j (spend_j)
```

To maintain simplicity we do not recommend any additional interventions in the Spend Track to promote higher-quality spends.

#### Buy Track

While the Buy Track incentivizes developers to drive Kin bought by getting their users to consume ads, many users are unaware that their attention is being exchanged to purchase Kin. Users are often not directly rewarded for their ad watches. We recommend increasing the requirements of developer's use of Buy Modules whereby users must be rewarded directly.

```
Let KRE_buy be the total amount of Kin paid to developers for the Buy track in a day.
Let buy_i be the total amount of Kin purchased and sent to users in app i in a day.

Then the buy payout for app i is:  
Payout_buy_i = min(KRE_buy * buy_i / (sum for all apps j buy_j), buy_i)
```

All Kin purchased and sent to users must be through earn transactions which have memo fields as follows:
*1-app_id-mod_id* i.e. *1-lipz-kads*

Users may only be rewarded for ads they themselves watched or Kin they themselves bought. 
In the case of an audit, either the app developer or module developer must be able to demonstrate that a specific user receives Kin for ads that they themselves have watched or Kin they invidually purchased via fiat dollars.
Either the app developer or module developers will also be required to demonstrate Kin was purchased on the open market and sent to the developer.

Module submission as described in KRE 2.2.2 will remain with the exception of the following line which should be removed to avoid confusion:

*- The user/developer are paid Kin at a rate at most 3x the market rate (i.e. a user can earn the developer at most $0.03 worth of Kin for an ad generating $0.01 of revenue, and a user buying $1.00 worth of kin cannot receive more than $3.00 worth of Kin).*

### Option ii. Active User Balances

The KRE payout logic would be replaced with the following simple logic:
```
On a given day, payout for app i will be:

Payout_i = (AUB_i / AUB_total) * KRE_total

Where:
AUB_i = min(Sum of user balances over all MAS in app i, 100000*number of MAS in app i)
AUB_total = Sum for all apps j (AUB_j)

A user is an MAS in app i if they have spent Kin in app i in the last 30 days.
The monopoly clause from the current KRE would still apply.
```

While Option i. addresses some of the core challenges of the KRE, it is still very complex making it difficult for developers to participate effectively and for operators to execute payouts. Active User Balances removes all of this complexity, turning the KRE into a simple and compelling game to play.

Fundamentally, the purpose of the KRE is to reward developers based on their contributions to the growth of the Kin Economy. If we define the Kin Economy as Kin used by individual users in the ecosystem, then Active User Balances is the simplest way to measure each developer's contribution to the total economy.

We understand that this implementation is a significant divergence from previous KRE implementations that rewarded specific user behaviour. In our assessment, rewards based on specific user behaviours have led to the increased complexity of the KRE and increased vectors of gameability. KRE 2.0 incentivizes a variety of use cases. Many of these, like Kin Ads, are productive in driving positive demand for Kin on the open market. However, there are also many use cases that do not drive demand for Kin and are therefore a net negative on the value of Kin. This is not the product of any bad actors in the ecosystem, but is instead a function of the current incentive structure. 

The goal of the KRE is to incentivize productive economic behaviour within the ecosystem, so as we evaluated options for future implementations we wanted to lean into options which incentivized such behviour and and/or reduced the incentive for unproductive behaviour. The best implementation will push developers to get their users to buy Kin and keep that Kin in the app economy to exchange between other users. This proposed algorithm incentivizes this exact behaviour as developers are encouraged to have as much Kin as possible in user wallets and have those users continuing to spend Kin.

We recognize that this may incentivize developers to “recycle” prior KRE payouts back into their app economy by giving it to users to “game the system” in order to maximize future payouts. There are three reasons why this behaviour is actually okay. 

1. The developer must ensure that the users continue to spend and keep the Kin within the app’s ecosystem. 
1. This KRE payment that was distributed to users is now Kin that can not readily be sold.
1. If a developer exclusively fuels their economy with KRE payouts then other developers can gain ground on this developer by getting their users to buy Kin, or by purchasing Kin themselves on the open market.

The best option for a developer is to get users to buy kin with their own attention/$ and keep it within the economy. The developer can keep all of their current payouts (and sell them if they'd like) while increasing their future payouts. Removal of the buy track also removes all issues with the track in its current form: users are often unaware they are "purchasing" Kin. Another criticism would be that this does not have a hold track, thus removing the incentive for developers to hold KRE payouts for as long as possible. We argue that while some developers chose to hold KRE payouts, a majority of KRE payouts in 2020 were sold despite this Hold Track incentive. While there is still incentive to not sell KRE payouts, this incentive is shifted and instead pushes developers to move Kin into their app-economies: a developer can increase their payouts by growing user balances in their app.

## Implementation
In either the Active User Balances option or the KRE 2.2.2 Extension option we recommend these changes take effect January 1, 2021.
The only exception to this would be the changes to the Buy Track in the KRE 2.2.2 Extension Option. These should be delayed in the event that no publicly available Ad or Buy Module which complies with the KRE is available in the near future.
Specifically, we recommend the Buy Module changes take effect no less than 21 days after such a module exists.

