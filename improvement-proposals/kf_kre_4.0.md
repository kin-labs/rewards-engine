# KRE Improvement Proposal
The purpose of this document is to propose updates to the methodology and rules used for the Kin Rewards Engine.

*versioning:*
- KRE 4.0

## Proposed by:
Kin Foundation

## Abstract
To stimulate the economy, this proposal provides incentives for apps to (1) build higher quality use-cases; and (2) create more economically meaningful transactions. 
While the community may be familiar with many of the concepts in the proposal, their definitions in some cases have been reworked.  There are also a number of new concepts to understand such as: a new method for ranking app performance based on an app’s overall economic contribution, a time limited boost for apps who are new to the Kin Ecosystem and a curving formula for the reward distribution which replaces the monopoly clause.

## Implementation
Implemendation date to be announced after technical upgrade is completed. 

### Contents

 1. [The Daily Payout](#daily-payout)
 2. [The Rewards Algorithm](#kre4)
 3. [Explanation of the Algorithm (in steps)](#explanation)
 4. [How do the minimum transaction thresholds work?](#thresholds)
 5. [How is the quality rating of an app determined?](#quality-rating)
 6. [Practical tips to achieve high rewards](#tips)


##  <a id="daily-payout" />1.  The Daily Payout

The total amount of Kin paid to developers for a day is _daily_payout_. It is based on a daily budget and is adjusted based on the volatility of the price of Kin.
  

```

daily_budget = 250,000,000 Kin

daily_payout = daily_budget * (1 - VA)

```

Where `VA` (the volatility adjustment) is a number ranging from 0 to 1 which represents the average amount of volatility in the price over the last 30 days.

More formally, it is the absolute average deviation over the last 30 days divided by the average closing price over the last 30 days.



   $$VA = \frac{1}{30}\sum_{p\in P} \frac{\lvert p-\bar{p} \rvert}{\bar{p}}.$$
    

Where,

 <img src="https://render.githubusercontent.com/render/math?math=P" alt="P"> is the set of closing prices in the last 30 days. 
 <img src="https://render.githubusercontent.com/render/math?math=\bar{p}"> is the average price in the last 30 days.


CoinGecko is used for closing price information in <span>$</span>USD. Each KRE payout will pay for a week of activity and have the same KRE_total. The week of dates `[x:x+6]` will be paid on or about date `x+24` and use price information from dates `[x-10:x+19]`. I.e. payouts for the week of Nov 15-21 will be paid on or about Dec 9 and use payout information from Nov 5-Dec 4 inclusive. Note that is not a change in payout timing from the current process.

  

The volatility adjustment is an algorithmic means to control the rate at which new Kin enters the market during times of volatility. If the price rises, and developers sell a constant percentage of their KRE payouts, then there may be insufficient market liquidity to absorb the increase in sell pressure causing dramatic swings in price. When the price is falling, it makes sense to tighten the flow of Kin in order to restabilize the price. In either of these situations, we can use the size of the KRE payouts to balance the economy.

  

Note that a developer will only be rewarded KRE payouts for days where at least one Kin blockchain transaction took place in their respective application.

  

## <a id="kre4" />2.   The Rewards Algorithm

### Economic Contribution Score
  
Developers are paid the _daily_payout_ based on their _Economic Contribution Score_ (**ECS**).   The ECS is a daily score for each app which aims to determine which app(s) brought the most valuable contribution(s) in driving Kin's token economy.  An ECS is calculated by using many metrics, such as the number of active users within the app, the amount of Kin spent by those users, their average user balances, the app's quality rating and more.  This section describes the technical aspects of the algorithm in detail while the following section describes the steps in plain english.

On a given day, payout for app *i* will be:

$$Payout_i = f \left( \frac{ECS_i}{\sum_j ECS_j} \right) * Daily\_Payout$$

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://i.imgur.com/Y57IHxk.png">
  <source media="(prefers-color-scheme: light)" srcset="https://i.imgur.com/xutkE7b.png">
  <img alt="KRE 4.0 formula breakdown" src="https://i.imgur.com/xutkE7b.png" width="80%">
</picture>


### Variable Definitions 

-   _AU<sub>i</sub>_: number of Active User in app _i_.

-   _AUB<sub>i</sub>_: total balance from Active User (above the AUB Threshold) in
    app _i_.

-   _MB<sub>i</sub>_: median balance from Active User in app _i_.

-   _MS<sub>i</sub>_: median spend (above the Spend Threshold) from Active User in
    app _i_.

-   _r<sub>i</sub>_: is the quality rating of app _i_ published by Kin Foundation.
    _r<sup>l</sup>_ and _r<sup>h</sup>_ are upper and lower bound of the quality multiplier,
    currently at 0 and 2. As examples, _r<sub>i</sub>_ = 0 (resp. _r<sub>i</sub>_ = 1.5)
    means that the app will get 0 (or 50% bonus) reward in the relevant
    period.

-    _c_: cap on the maximum balance from an Active User in calculating
    _ECS<sub>i</sub>. Proposed to be increased to \$10* _exchange\_rate_ between
    USD and Kin.
    
-   _J<sup>*</sup>_ is the set of apps whose AU passes a minimum threshold, among which the min’s and max’s are
    taken. This is to ensure that the median balance and median spend of an app is meaningful and can
    therefore serve as benchmark of normalization for the _κi_'s. The threshold is set by the Kin Foundation.

-   _a_: minimum threshold on _AU<sub>i</sub>_ to determine the set of apps that
    will be used for the normalization of the three scores (_s<sub>i</sub><sup>AU</sup>,s<sub>i</sub><sup>MB</sup>,s<sub>i</sub><sup>MS</sup>_). Currently set at 500.

-   _P_ is the set of closing prices in the last 30 days.  <img src="https://render.githubusercontent.com/render/math?math=\bar{p}"> is
    the average price in the last 30 days.
    
-   The curving and monopoly clause function can be adjusted as needed.
    Currently, it is set as:   
    
    $$f(x_i)= g(x_i)^{0.5}/\sum_J g(x_i)^{0.5} where  g(x_i)= \frac{2999}{3000}\cdot x_i + \frac{1}{3000}\cdot \max_i(x_i).$$

    Intuitively, _g(x<sub>i</sub>)_ applies a curve to app _i_'s relative ECS to give extra Kin to smaller apps. _f(x<sub>i</sub>)_ then applies a diminishing return on the contribution of relative ECS on the final payoff; the exponent (<img src="https://render.githubusercontent.com/render/math?math=\in[0,1]">) governs the concavity of this function, and a
    smaller value means a more severe diminishing marginal return.

-   Active User: a wallet which has spent the Spend Threshold in a
    single transaction during the last 30 days.

-   AUB Threshold: an economically meaningful AUB amount, which is
    updates by the Kin Foundation (every second month). Currently set at
    3 times the USD cost of creating a SOL wallet.

-   Spend Threshold: an economically meaningful spend amount, which is
    published by the Kin Foundation every second month. Currently set
    at 1 cent (USD) multiplied by the _exchange\_rate_ between USD and Kin. May be
    increased to be 5 cents X  _exchange\_rate_ through further updates.

-   _VA<sub>i</sub>_: is the volatility adjustment meaning a number ranging from 0
    to 1 which represents the average amount of volatility in the Kin
    price over the last 30 days. More formally, it is the absolute
    average deviation over the last 30 days divided by the average
    closing price over the last 30 days.
  
## <a id="explanation" />3.  Explanation of the Algorithm (in steps) 
  
  
Developers earn their share of the daily_payout based on their Economic Contribution Score. To calculate an app’s ECS the formula will take the following steps:  
  

1.  The first step evaluates the number of active users of the app and the relative size of the user economy connected to it.  An active user is one who has spent more than the Spend Threshold worth of Kin (set at 0.01C) within the app in the last 30 days in a single transaction. This can be either by a user-to-developer transaction or a peer-to-peer transaction. Then, the total amount of Kin held as balances from these active users is recorded for the ECS. There are two additional balancing factors in this step, trivial user balances holding less than 3x the user wallet creation cost are ignored, and the maximum user balances for the app is capped at $10 worth of Kin multiplied by the total number of active users of the app. Essentially, this first step gives a measurement of the size of the Kin user economy connected to the app.
    
  
2.  The number arrived at in step 1, is then adjusted by a composite score based on the median of three scores (number of active users, median balance and median spending). These scores are normalized meaning each number is a figure between 0 and 1. What this is doing is benchmarking the performance of each app against each other to see which apps have, for example, more active users or have created a use-case where their users are spending more. The median is used because it will encourage an app to be good in any two of the three metrics - which will assist in making a more competitive playing field amongst different use cases. For example, an app may have less active users, but their users spend more and on average hold more Kin than other Kin apps. When these figures are normalized, the activity of apps which have less than 500 active users are not taken into account so they do not skew the benchmarking.  This step 2 is weighing up the app's Kin user economy against the app's use-case performance (in comparison to other apps).
    
3.  After this, the app’s quality rating is considered by the formula. Where an app can demonstrate it has met the Kin integration standards, then it can boost its ECS. This may make the app more competitive in the KRE against its peers because it offers more features or functionality the Kin community generally would expect. To obtain the quality rating, the owner of the app undertakes a self-assessment in the Kin Developer Portal and responds to different questions about their Kin use-case. The responses will be made available to the Kin community to promote accuracy and community governance. The initial questions are detailed below.  
      
    
4.  For new apps only - New apps with active users but low median balance may be hurt by the formula initally.  The proposal is that new apps with at least 500 active users receive a time limited boost for their first two months which applies from the date they register for the KRE. This works by assigning the app the median ECS among the ecosystem apps in the Kin ecosystem (instead of 0). After this time, the boost is switched off and they will need to compete based solely on their own performance.
  

At this point, the ECS for each app is known. The engine will begin preparing the payment however before sending it, some final checks and balances are made:  
  

5.  The daily reward payment is adjusted by the volatility of the Kin price in the last 30 days. This is an algorithmic means to control the rate at which new Kin enters the market during times of volatility. If the price rises, and developers sell a constant percentage of their KRE payouts, then there may be insufficient market liquidity to absorb the increase in sell pressure causing dramatic swings in price. When the price is falling, it makes sense to tighten the flow of Kin in order to restabilize the price. In either of these situations, we can use the size of the KRE payouts to brace the economy.  
      
    
6.  Lastly, the payment is distributed on a curving formula of an app’s relative ECS to others. This ensures that smaller apps continue to receive rewards and larger apps find it difficult to become a monopoly over the payments.
    

  

## <a id="thresholds" />4.  How do the minimum transaction thresholds work?

  

This proposal contains threshold amounts for certain metrics to be counted for the purposes of the rewards engine algorithm. This will encourage more economically meaningful transactions across the ecosystem. We propose the thresholds are re-calibrated on the first day of every second calendar month following the implementation date and rates will be published by the Kin Foundation to the Kin.org website.

 Example thresholds if:  
```
 - Kin price is: 0.000012 USD
 - Sol price is: $42.91 USD
 - Cost of creating a Rent-Exempt Wallet on the Solana Blockchain is: 0.00204928 SOL  
 ``` 
| Kin performance metric | Description | Calibrated to: | Kin Threshold Amount |
|--|--|--|--|
| AUB Minimum Threshold | The minimum Kin user balance required of an Active User to be recorded as AUB. | 3x the cost of rent-exemption on the Solana Blockchain  | 7328 Kin
| AUB Cap for an App | The maximum amount of Kin which can be counted towards AUB for the app as a whole. | $10 worth of Kin  (multiplied by the number of active users of the app) | 833,333 Kin
| Minimum Spend | The minimum spend amount needed to be made by an active user to be counted as a spend transaction. | 0.01c USD worth of Kin.| 833 Kin


 Effectively in this example, the app would need each user to spend 833 Kin or greater and users to hold at least 7328 Kin in their wallets for those activities to be counted for the purposes of the rewards algorithm . If an app has 50K active users, its maximum AUB would be 41.6 billion Kin before the algorithm would cap this metric.

  

## <a id="quality-rating" />5.  How is the quality rating of an app determined?

  

Apps are assessed on the quality of their Kin integration which contributes to the app’s overall ECS. As per the definition of _r<sub>i</sub>_, the quality rating score acts to boost an app’s ECS where the score is positive. The Kin Developer Portal will ask developers to self-assess their own app through a series of questions and the responses are used by the KRE to calculate the app’s quality rating. To begin with, the self-assessment questions will be objectively determinable in nature and easily verifiable from a cursory examination of the app. The wording of the self-assessment questions should be unambiguous to remove any subjectivity in submissions.  The self-assessment questions as at the implementation date are proposed to be as follows:

 - Can your end-users **see their Kin public wallet address** within your app?
 - Can your end-users **copy their Kin public wallet address** to their device’s clipboard?
 - Are your end-users able to **export the private key** of their in-app Kin wallet address?
 - Can end-users **import or connect an external Kin wallet** to be used as the primary wallet within your Application?
 - Do you permit end-users to **deposit Kin** to their in-app wallet balance?
 - Do you permit end-users to **withdraw 100% of their Kin** balance from the app? (If you only enable partial withdrawals or you impose a withdrawal fee you must answer no).
 - Does your app **contain a tutorial or introduction** for first time end-users to learn more about Kin, with a visible written hyperlink to “www.kin.org”?
 -  Does your app integrate a fiat-to-crypto payment solution from **Ramp, Simplex, Wyre or MoonPay** which enables your end-users to purchase Kin?
 - Does your app incorporate the **Kin logo** as a currency symbol in all places where Kin can be spent by your end-users?

To ensure accuracy, the KRE will impose a cumulative penalty on the app's KRE payments where an incorrect response is detected. To promote community governance over the KRE, the responses are intended to be made public and the relevant Kin community member will earn the accrued penalty fee as a reward when they are first to report an accepted issue.   The penalty shall be a minimum of 10% commencing on notification to the app owner and increase at a rate of 0.2084% per hour until the app owner has resubmitted accurate responses through the Kin Developer Portal (i.e. this penalty is 15% after 24 hrs and would be 45% after 7 days if left outstanding).  As this is a new process, within the first 60 days of implementation only a grace period of 48 hours will be offered to update responses before any penalty is imposed. 

The Kin Foundation may update, modify, remove or supplement any of the above questions at any time based on Kin user feedback however an app’s rating will not change until it has resubmitted updated responses following such changes so it not prejudiced by changes to the questions of which it was not aware.


## <a id="tips" />6.  Practical tips to achieve high rewards

  
Practically, for an app to perform well in the Kin Rewards Engine it should focus on creating a user-experience which:  
  

-   Users are incentivized to spend Kin on meaningful experiences within the app.  
      
    
-   Provide tiered systems of rewards or user benefits, which encourages users to save up their Kin balance or use a buy-module to purchase higher value goods, services or experiences, as the case may be.  
      
    
-   Include as many Kin integration standards as possible to create the best user experience for your users and boost the app’s ECS.  
      
Additonally, apps should be aware that as the price of Kin trends upwards, the Active User Cap will be trending down.  This means as the cap tightens, apps should focus on user engagement, use-case and quality of integration to get the edge over near ranking competitors. 

We recommend providing a buffer to the value of the threshold amounts wherever possible to avoid having to update the app for granular updates to the threshold amounts. I.e. it is not necessary that a user spend exactly 1c worth of Kin, you may for instance focus your use case on encouraging users to spend dollars-worth of Kin.

More tips are regularly published to the Kin Developer Documents, make sure to check them regularly. 
