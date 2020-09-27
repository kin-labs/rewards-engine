## Kin Improvement Proposal
The purpose of this document is to outline a proposed new version of the KRE Algorithm

## Abstract
The KRE has gone through several changes, and each change has improved upon its predecessor, and also revealed new avenues for refinement. Each itteration tries to solve for the following:

1. Incentivize users to spend more Kin (economic spread and depth)
2. Incentivize users to buy more Kin (market value)
3. Incentivize developers to hold Kin (market value, ecosystem commitment)


## Summary of Improvements
1. KRE Algorithm Updates

 - Simplification of Spend track
 - Simplification of Buy track
 - Improvement of Hold track

The improvement proposal follows a short discussion below:

## Kin Ecosystem
Unlike most other crypto-currencies, which derive value from speculation and buy pressure from expected future rewards, Kin focuses its incentives on apps, which are analogues to miners and minters. Like miners, Kin apps do productive work, and are rewarded with Kin which propagates to the rest of the ecosystem. So far, this has been hugely successful in drawing Kin from the KRE and distributing it to users.

![Kin](https://i.imgur.com/cKtxrRD.jpg)

This proposed itteration improves the current one by increasing the pull of KIN from exchanges, and pushing it leftward, into a growing economy of ready users. 

### Current Mechanism
The current mechanism has driven this process, but has encountered the following challenges:

1. Given intricacy of the calculations, it is difficult for devs to get a 'gestalt' of their position in the game, and their next best action to improve their rankings. (Should they optimize for buy/hold/transactions, etc)
2. The most an app can earn from the buy track is the max amount of Kin it bought.
3. The hold track needs to be more appealing to apps and ecosystem.

## KRE Algorithm Updates
This proposal addresses these issues, while also making the KRE calculation simpler. There are five variables to consider:

1. A = Total Kin released for the spend track.
2. B = Total Kin released for the buy track.
3. GDP<sup>i</sup> = GDP for app *i*. (Total volume of transactions)
4. Hr<sup>i</sup> = Hold ratio for app *i*. (Total Kin it holds / Sum held by all apps)
5. Br<sup>i</sup> = Buy ratio for app *i*. (Total Kin from buy module / Sum bought by all apps)

The reward attributed to app *i* of *n* total apps for a certain period becomes:


![Reward](https://i.imgur.com/PdWkfx0.jpg)


An app is rewarded for having a high GDP *(GDP<sup>i</sup>)*, a high buy ratio *(Br<sup>i</sup>)* and a high hold ratio *(Hr<sup>i</sup>)* relative to other apps. Note that the hold ratio acts as a multiplier for an app's potential rewards.

### Notes:
**GDP**

The current mechanism segragates spends - E.g. 1-9|10-99|100-999| etc. This proposal allows apps to simply focus on maximizing the number of trades and volume of trades, while still increasing Kin's economic GDP. Naturally, a cap can be put on the largest permisible trade to be 1,000 Kin. Even with this simplification, an app with higher average volumes (e.g. 500 Kin per transaction) is rewarded more than one with lower average volumes (e.g. 100 Kin per transaction).


**Buy ratio (Br)**

As long as an app is buying Kin and funneling it into the economy, no limit is placed on the amount of rewards it can earn by increasing buy pressure. This allows apps to use buy modules more profitabley.


**Hold ratio (Hr)**

The Hold ratio is like a stake in the economy. For two apps that have the same volume of transactions, and the same buy ratio, the app that holds more Kin recieves a higher reward.

To enable small apps to compete in terms of holding, the equation can be modified to use a log or root of the hold ratio. This smooths out the reward curve and prevents monopolization of the hold track by large apps.


![Reward curve](https://i.imgur.com/uRvDWHm.jpg)


**Spend track and Buy track (A,B)**

These can be adjusted over time, to match the ecosystem's needs.

### Discussion
The proposal aims to keep the reward mechanism simple, while also incentivizing GDP growth and driving Kin from exchanges into Kin's economy.

It also encourages apps to hold Kin, and rewards those with the bigger stake in the ecosystem. Implemented, the new reward curve would resemble the current curve, in that the rankings would not change significantly.

However, it would simplify how apps understand the reward system, and it would incentivize a new game to use the buy modules, and also to hold Kin for the benefit of the entire ecosystem.

## Implementation
There are two variables to adjust over time. This can start with the rewards weighted heavily for the Spend track (A) and, over 3 months, transition to a more even distribution as more apps implement buy modules.

| Month           | Spend Track A % | Buy Track B %   |
| --------------- | --------------- | --------------- |
| 1               | 90              | 10              |
| 2               | 80              | 20              |
| 3               | 60              | 40              |
