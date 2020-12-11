## Kin Improvement Proposal - KRE V3.0 (Cap)
The purpose of this document is to outline a proposed new version of the KRE Algorithm

## Proposed by: Kik Interactive Inc. 

## Abstract
The Kin Rewards Engine (KRE) is the primary mechanism that the Kin Foundation uses to allocate the Kin Reserves in order to drive growth of the Kin Economy. In order to build and sustain the Kin Economy, the Kin Foundation must carefully choose the KRE payout size in order to make KRE participation compelling for developers while not flooding the market with Kin. We present 3 options for daily KRE payout caps to start on January 1, 2021:
1. KRE Payouts are capped at the lesser of 250,000,000 Kin and $1 * MAS / 365 in Kin
1. KRE Payouts are capped at the lesser of 250,000,000 Kin and 2% of the 24 hour trading volume in Kin
1. KRE Payouts are capped at 250,000,000 Kin * (1-VF). VF is a newly defined volatility factor which ranges from 0 to 1 and represents the average amount of volatility in the price over the last 30 days.

Our recommendation is Option 3: basing the payout cap on Kin price volatility.

## Introduction

The payout cap of the KRE is one of the most important variables in the entirety of the algorithm. It is the primary determining factor of both how compelling the KRE is for developers and the rate at which inflationary Kin enters the economy. Additionally, any payout cap must ensure that all Kin Stakeholders are aligned with the long-term best interests of Kin. This is a challenging balance. Our intention with this proposal is to optimize for the long term value of Kin. It is through this lens that we present these options and this recommendation.

At the time of writing, Kin is facing challenges with limited liquidity on exchanges. Kin has an [average trading volume of $156,000](https://www.coingecko.com/en/coins/kin/historical_data/usd#panel) over the past 30 days, and a current market cap of $60 million.
When comparing to other similarly-sized projects in terms of market cap, [Wax](https://www.coingecko.com/en/coins/wax/historical_data/usd#panel) and [Steem](https://www.coingecko.com/en/coins/steem/historical_data/usd#panel) have considerably higher 24 hour transaction volumes of $1.6 million and $7.1 million respectively. With more than 2.5 million monthly active spenders, Kin is no longer a brand new project requiring large injections of economic stimulus to kick-start the economy. Considering this, and the fact that the liquidity of Kin remains low, we believe the Kin Foundation should be modest with KRE payouts in the near future. This is especially important in the case of a price appreciation for Kin as large amounts of dollars of Kin newly entering circulation with limited liquidity could cause significant price swings.

In November, we proposed a payout cap in our KRE 3.0 recommendation: *250 million Kin or $USD 5000 in Kin, whichever is less.* While this option would create a safe buffer for Kin's liquidity challenges, we received feedback that the fiat component of the cap could create less desirable incentives for developers. The cap would create an incentive for developers to want the price of Kin to be as low as possible for as long as possible (to keep payouts large in terms of number of Kin) and then rise later, creating misaligned incentives. Moreover, competing for a piece of $5000 / day may not be enough to get new bigger apps to join the KRE. Even if one such app were to join, and drive significant demand for Kin, other apps would be competing for strictly less dollars worth of Kin with no potential upside. For these reasons, we went back to evaluate options for a payout cap that helped with our short-term liquidity issues, while making sure all invested parties remain aligned.


We have considered 3 different means of determining what the payout cap should be:
1. MAS cap (the size of the ecosystem)
1. Liquidity Cap (the amount of liquiditiy in the market)
1. Volatility Cap (how volatile the price of Kin is)

Our recommendation is the last option, basing the payout on the volatility of the price of Kin. We feel this aligns the incentives of participants and remains relatively closed to attack vectors. We would recommend the Kin Foundation monitor the ecosystem and plan to make adjustments to the cap quarterly (or more frequently in the case of dramatic changes) based on material impact to any of the three variables listed above. This could include increasing or decreasing the cap.

## MAS Cap

A simple way of determining the amount of Kin that should be paid by the Kin Foundation is by looking at the size of the Kin Ecosystem. Monthly Active Spenders (MAS) is the simplest measure of this. One can argue that the Kin Foundation should cap payouts based on the Average Revenue Per User. Specifically, we can look at MAS versus KRE payouts in $USD. 

Suppose the Kin Ecosystem has 3 million MAS and the KRE pays out $5000 a day in Kin. The Average Revenue Per MAS Annually is then: `$5000 * 365 / 3,000,000 = $0.61`. Market analysis would indicate that there is a large range in Average Annual Revenue per MAU all the way from [$0.28](https://www.businessofapps.com/data/reddit-statistics/) on Reddit to [$29.25](https://s21.q4cdn.com/399680738/files/doc_financials/2019/q4/Q4-2019-Earnings-Presentation-_final.pdf) on Facebook. Because of Kin's current liquidity issues, we would recommend a more modest cap of Average Revenue Per User Annually at $1.00 / MAS. Working backwards, this gives us a simple formula of:
```
KRE_total = min(250,000,000, $1 * MAS / 365 / Kin_price)
```

Where `MAS` would be the MAS of the date in question and Kin_price is the 7-day trailing average of the Kin price in $USD as listed on CoinGecko. I.e. if MAS was 3 million, KRE_total would be the lesser of 250 million Kin and $8219.18 in Kin, whichever is less.

While this cap could allow for larger developers to join the ecosystem, it still has misaligned incentives with existing developers and price: if MAS does not grow, then developers may still want the price to stay low. For this reason, we do not recommend this option.

## Liquidity Cap

Another argument for the daily payout size can be made by basing the payout cap directly on market liquidity. Essentially, the more liquid the market, the more easily KRE payouts can be absorbed without massive swings in price. Using projects like WAX and Steem as a comparison, we would recommend a daily cap that is at most 2% of the 24-hour transaction volume.
```
KRE_total = min(250,000,000, 2% * kin_liquidity)
```

Where `kin_liquidity` is the 24 hour transaction volume with any fraudulent activity removed. While this option is very direct, it has potential attack vectors. It is very easy to pass Kin back and forth between wallets, making the market appear more liquid than it actually is. The Kin Foundation would likely need the assistance of a 3rd party service in order to accurately measure real liquidity in the market, and mitigate against the potential for fraud. For this reason, we do not recommend this option.

## Volatility Cap

While examining options, we realized that what we really wanted was an algorithmic means to control the rate at which new Kin entered the market during times of volatility. If the price rises, and developers sell a constant percentage of their KRE payouts, then there may be insufficient market liquidity to absorb the increase in sell pressure causing dramatic swings in price. When the price is falling, it makes sense to tighten the flow of Kin in order to restabilize the price. In either of these situations, we can use the size of the KRE payouts to brace the economy.

This leads us to our recommendation of a payout cap based on price volatility:
```
KRE_total = 250,000,000 * (1 - VF)
```
Where `VF` (the volatility factor) is a number ranging from 0 to 1 which represents the average amount of volatility in the price over the last 30 days.
More formally, it is the absolute average deviation over the last 30 days divided by the average closing price over the last 30 days.

![VF Equation](https://i.imgur.com/LGDyTYm.jpg)
```
Where,
P is the set of closing prices in the last 30 days.
p_avg is the average price in the last 30 days.
```

Note that since VF will always be a number between 0 and 1, KRE payouts will always be at most 250 million Kin. For reference, if this method had been used in 2019, the average daily payout would have been 208 million Kin and the minimum daily payout would have been just under 100 million Kin.
CoinGecko will be used for closing price information in $USD. Each KRE payout will pay for a week of activity and have the same KRE_total. The week of dates `[x:x+6]` will be paid on or about date `x+24` and use price information from dates `[x-10:x+18]`. I.e. payouts for the week of Nov 15-21 will be paid on or about Dec 9 and use payout information from Nov 5-Dec 4 inclusive. Note that is not a change in payout timing from the current process.

In order to demonstrate what this cap does we look at 3 examples: if the price is very stable, if the price is rising, and if the price is falling. If the price is reasonably stable then the deviation in prices will be small, VF will be very close to 0 so payouts will be close to 250 million Kin. If the price is rising then VF will be higher, so the number of Kin paid out will decrease in the short term while the price is shifting. If the price stabilizes at a higher value, the amount of Kin being paid out will rise back to 250 million Kin. This lag gives time for the market to adjust to the increase in price. Finally, if the price is falling, then KRE payouts will similarly decrease. This decrease should help dampen the drop while our liquidity remains an issue.

This cap creates alignment among the entire ecosystem to drive towards a strong Kin currency. Additionally, unlike the 2nd option, it is reasonably simple to calculate without any 3rd party assistance and is very challenging to manipulate over the long term.

## Implementation
We recommend these changes take effect January 1, 2021 with the introduction of KRE 3.0.
