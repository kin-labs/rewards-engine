# Reputation Model Proposal

## Introduction

As we interpret it, the reward engine proposed is basically a PoS model with 2 key features:

1. The distribution model is both, known to all and deterministic. Any reward engine one might think of is vulnerable to attacks and abuse. Keeping the model semi-transparent will make it much more prone to these attacks. If secrets aren't desired due to fear of centralization, we would suggest adding randomness to the model. Specifically, in the model proposed, a simple bribery attack is possible - (relating to the example in the RFC file) `Daniel` could pay `Kaitlyn` a small bribe for her to transact with him, leading to him sweeping the majority of the reward that day. In addition, even if `Kaitlyn` is an innocent user, her power is overwhelming - her vote is practically the only one that matters.

2. Not a one-coin-one-vote mechanism. As shown in the example some coins may not count towards the reward. This might seem ok, but it allows another abuse - it allows coins to count more than once. If, for example, `Emma` opens a new Kin wallet - `Emma2` - with 0 Kin and after doing all her transactions from the original `Emma` wallet she transfers her remaining 500 Kin to the new `Emma2` wallet and then transacts again with the ecosystem, her coins will count twice, distorting the original intent of the reward engine.


## Proposal

We believe a reputation system run by Kik is not only possible, but inevitable, at least so long as the system is in bootstrap mode and a more stable PoS mechanism is found. The reputation model is made possible due to one key observation, namely, that most users interacting with the Kin ecosystem will do it from the Kik messenger app (at least in the early days). Assuming there will be an option to get a Kin wallet within the app (or to incorporate an existing one with it), a link can be made between devices and Kin addresses. This mapping will allow a reputation model based on a one-device-one-vote basis. Here is a possible start of such a reputation system.

It will apply to both users and developers (i.e., similarly to Uber's drivers' and passengers' reputation), which:

1. Will be weighted during users' voting and calculation of developers' rewards.
2. Will be used to incentivise behaviors we would like to promote, while punishing bad acting (reduce Sybil attacks, promote participation and spending, etc.).
3. Will be individually visible to users (without the actual derivation, probably) in order to achieve the above.
4. Everyone would be able to verify that the rewards are being distributed correctly and according to the pre-defined rules. We will periodically publish and explain what behavior increases/decreases the reputation, in order to incentivise good behavior, but won't necessarily share how is it calculated exactly.

### Guidelines

1. Developers will be identified entities. Their reputation will be calculated according to the quality of their KYC, the detail of their app plan, the marketing that they do, etc.
2. Users are anonymous so this is more tricky. However, as explained earlier this can be mitigated as long as users link their wallets and participate in the ecosystem via the Kik messenger (and this is the key realization that makes reputation feasible).  Reputation will be given to each Kin address depending on things like:
	* Whether the address is attached to the mobile app or not. In case it is, a lot of data is available - how long does the user have the app, how active is he, his age, occupation, etc. This can be calculated locally on the device and sent to a Kik server (to preserve privacy) or done on Kik's servers (if possible legally). E.g., the amount of addresses a certain device opened is super relevant to that user's reputation.
 	* Age of coins. The longer the coins sit in an address the more likely they are trustworthy.
 	* Age of address. E.g., a new address will have reputation 0 and will be completely ignored by the reward engine (unless it was opened in a wallet of a specific type of user). The age of the address will be calculated either using its creation time (when available; e.g., contracts) or when the first incoming transaction has happened.
	* Interaction with many developers (an address interacting with plenty of developers is highly likely to be honest).
	* And more...

The final score of a developer will be calculated as a weighted sum of his reputation, his users' reputations, and a regularization parameter that makes sure too sudden changes aren't possible (a developer doesn't become super popular in one day).

### Other Ideas to Consider

1. Anti-fraud - Kik will analyze Kin's transactions' graph to find fraud, e.g. Kin tokens that are being transferred from a developer to himself or any other circular references. There are pretty effective clustering mechanisms which already exist on the Bitcoin blockchain, in addition to lots of fraud detection technique which will apply in our case as well. Not sure how effective they are on Ethereum/ERC20 tokens, but worth researching it.
2. Frequency - We are not sure a daily distribution is the best way to go. The distribution should match the activity on the system in some sense. For example, we could say a distribution takes place once a specified amount of Kin was transferred (again, only by reputable users). The amount of the distribution can be determined according to the amount of days since the last one took place.
3. Soft voting - in a soft voting mechanism a user can vote for many developers according to his interaction with each of them. In addition, the distribution of a user's vote among many developers should not be linear in order to minimize gaps and thrive to a more evenly structured vote. Finally, users normally have pretty repetitive patterns of interaction with such ecosystems and we can divide the daily sum a user has spent with his average spending on the platform to correct his weight in the reward formula (again, in order to minimize unwanted gaps between strong and early developers and weaker and newer ones).

This is just a draft and could and should be refined and improved significantly.

David Yakira ORBS
Leonid Beder, Kik
