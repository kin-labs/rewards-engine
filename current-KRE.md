# Kin Rewards Engine 

The purpose of this document is to provide an overview of the methodology and rules used for the Kin Rewards Engine.

## KRE 3.0

### The Daily Payout 
The total amount of Kin paid to developers for a day is daily_payout. It is based on a daily budget and is adjusted based on the volatility of the price of Kin.

```
daily_budget = 250,000,000 Kin
daily_payout = daily_budget * (1 - VA)
```
Where `VA` (the volatility adjustment) is a number ranging from 0 to 1 which represents the average amount of volatility in the price over the last 30 days.
More formally, it is the absolute average deviation over the last 30 days divided by the average closing price over the last 30 days.

![VA Equation](https://i.imgur.com/E9TotU3.jpg)
```
Where,
P is the set of closing prices in the last 30 days.
p_avg is the average price in the last 30 days.
```

CoinGecko is used for closing price information in $USD. Each KRE payout will pay for a week of activity and have the same KRE_total. The week of dates `[x:x+6]` will be paid on or about date `x+24` and use price information from dates `[x-10:x+18]`. I.e. payouts for the week of Nov 15-21 will be paid on or about Dec 9 and use payout information from Nov 5-Dec 4 inclusive. Note that is not a change in payout timing from the current process.

The volatility adjustment is an algorithmic means to control the rate at which new Kin enters the market during times of volatility. If the price rises, and developers sell a constant percentage of their KRE payouts, then there may be insufficient market liquidity to absorb the increase in sell pressure causing dramatic swings in price. When the price is falling, it makes sense to tighten the flow of Kin in order to restabilize the price. In either of these situations, we can use the size of the KRE payouts to balance the economy.

Note that a developer will only be rewarded KRE payouts for days where at least one Kin blockchain transaction took place in their respective application.

### Active User Balances

Developers are paid a portion of the daily_payout based on the total sum of all balances of all active users in their app.
```
On a given day, payout for app i will be:

Payout_i = (AUB_i / AUB_total) * daily_payout

Where:
AUB_i = min(Sum of user balances over all MAS in app i, 100000*number of MAS in app i)
AUB_total = Sum for all apps j (AUB_j)

A user is an MAS in app i if they have spent Kin in app i in the last 30 days.
```

### Monopoly Clause 

No single developer will receive more than 66.67% of the KRE payout for a single day and any developer that would have received more than 50% of the payout will have their payout adjusted.
No two developers will receive more than 90% of the KRE's payout for a single day.
In both cases, residual payouts will be redistributed proportionally to other developers.

Let `s_1, s_2, …, s_n` be the KRE payout shares ordered by payout proportion in descending order before invoking the monopoly clause.
```
If (s_1 + s_2  > 0.90) or (s_1 > 0.5):
    If s_1 > 0.5:
        s_1' = 0.5 + ((s_1 - 0.5) / 0.5) * (2/3 - 1/2)
    Else:
        s_1' = s_1
    If s_1' + s_2  > 0.90 then:
        s_2' = s_2 / (s_1+s_2) * 0.9
    Else:
    	s_2' = s_2
    s_1’ = minimum(s_1' / (s_1'+s_2) * 0.9, s_1')
    If s_2’ != s_2:
        For i = 3 to n:
            s_i' = s_i / (sum from i = 3 to n of s_i) * 0.1
    Else:
        For i = 2 to n:
            s_i' = s_i / (sum from i = 2 to n of s_i) * (1 - s_1')
	Developers are paid out based on s_i'
Else:
	Developers are paid out based on s_i
 ```

**Example 1:**  
Payout shares before clause: `{0.35, 0.3, 0.2, 0.15}`  
Payout shares after clause: `{0.35, 0.3, 0.2, 0.15}`  

**Example 2:**  
Payout shares before clause: `{0.90, 0.05, 0.03, 0.02}`  
Payout shares after clause: `{0.633, 0.183, 0.11, 0.073}`  

**Example 3:**  
Payout shares before clause: `{0.50, 0.45, 0.03, 0.02}`  
Payout shares after clause: `{0.474, 0.426, 0.06, 0.04}`  

**Example 4:**  
Payout shares before clause: `{0.55, 0.44, 0.01}`  
Payout shares after clause: `{0.486, 0.414, 0.06, 0.10}`

Payout shares before clause | Payout shares after clause
--------------------------- | --------------------------
`50%` | `50%`
`60%` | `53.33%`
`70%` | `56.67%`
`80%` | `60%`
`90%` | `63.33%`
`95%` | `65%`
