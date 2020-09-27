## Kin Improvement Proposal
The purpose of this document is to outline a proposed new version of the KRE Algorithm

## Abstract
The KRE has gone through several changes, and each change has improved upon its predecessor, and also revealed new avenues for refinement. Each itteration tries to solve for the following:

1. Incentivize users to spend more Kin (economic spread and depth)
2. Incentivize users to buy more Kin (market value)
3. Incentivize developers to hold Kin (market value, ecosystem commitment)

## Purpose
The incentive's purpose is to drive a healthy GDP and market value for Kin. Kin's economy is contrasted to the general crypto sphere below:

### Bitcoin protocol
![Bitcoin](https://i.imgur.com/iLIFAfD.jpg)

Most crypto-currency value is driven by speculation of expected future rewards, as shown above. Buy preasure is driven by exchanges, and currencies like Bitcoin have demand as the base currency for most of the trades.

### Kin
Kin focuses its incentives on apps, which are analogues to miners and minters.
![Kin](https://i.imgur.com/cKtxrRD.jpg)
For Kin to succeed, the incentive layer needs pull KIN from exchanges, and push it leftward, into a growing economy of actual users. 

## Current Mechanism
The current mechanism has driven this process, but has encountered the following challenges:

1. Given intricacy of the calculations, it is difficult for devs to get a 'gestalt' of their position in the game, and their next best action to improve their rankings. (Should they optimize for buy/hold/transactions, etc)
2. The most an app can earn from the buy track is the max amount of Kin it bought.
3. The hold track needs to be more appealing to apps and ecosystem.

## Proposal
This proposal addresses these issues, while also making the KRE calculation simpler. There are five variables to consider:

1. A = Total Kin released for the spend track.
2. B = Total Kin released for the buy track.
3. GDP<sup>i</sup> = GDP for app *i*. (Total volume of transactions)
4. Hr<sup>i</sup> = Hold ratio for app *i*. (Total Kin it holds / Sum held by all apps)
5. Br<sup>i</sup> = Buy ratio for app *i*. (Total Kin it bought / Sum bought by all apps)

The reward attributed for app *i* of *n* total apps for a certain period becomes:
![Reward](https://i.imgur.com/kj6f0nD.jpg)
An app is rewarded for having a high GDP, a high buy ratio and a high hold ratio relative to other apps. The hold ratio as as a multiplier for an app's potential rewards.

### Notes:
**GDP**

The current mechanism segragates spends - E.g. 1-9|10-99|100-999| etc. This proposal allows apps to simply focus on maximizing the number of trades and volume of trades, while still increasing Kin's economic GDP. Naturally, a cap can be put on the largest permisible trade to be 1,000 Kin.


**Buy ratio (Br)**

As long as an app is buying Kin and funneling it into the economy, no limit is placed on the amount of rewards it can earn.


**Hold ratio (Hr)**

The Hold ratio is like a stake in the economy. For two apps that have the same volume of transactions, and the same buy ratio, the app that holds more Kin recieves a higher reward.

To enable small apps to compete in terms of holding, the equation can be modified to use a log or root of the hold ratio. This smooths out the reward curve.
![Reward curve](https://i.imgur.com/C7OTtZx.jpg)

**Spend track and Buy track (A,B)**

These can be adjusted over time, to match the ecosystem's needs.

### Discussion
The proposal aims to keep the reward mechanism simple, while also incentivizing GDP growth and driving Kin from exchanges into Kin's economy.

It also encourages apps for holding Kin, and rewards those with the bigger stake in the ecosystem. Implemented, the new reward curve would resemble the current curve, in that the rankings would not change significantly.

However, it would simplify how apps understand the reward system, and it would incentivize a new game to use the buy modules, and also to hold Kin for the benefit of the entire ecosystem.