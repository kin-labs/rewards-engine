# Kin Improvement Proposal
The purpose of this document is to outline a proposed improvement to the existing KRE algorithm. 

*versioning:*
- *3.0.1*

## Proposed by:
*The Kin Foundation*

## Abstract
KRE 3.0.1 is an update which helps app developers manage Active User counts (AU) for their apps. The Active User count is used to determine a cap on the maximum Active User Balance (AUB) of kin an app can be rewarded for.

The current definition of the AUB cap for an app *i* is:
```python
100000*MAU
```

where MAU = Monthly Active Users for app *i*. A user is an MAU in app *i* if they have spent Kin >= 1 time in app i in the last 30 days. 

Generally, the MAU should be an analog of real users in an app, where the assumption is that one spending account correllates to an actual spending user in the app. This is expected to correlate with the number of users the app brings into the Kin Ecosystem, and more users leads to larger apps getting rewarded more for their contributions.

However, we have noticed that some apps may have trouble controlling this number, due to bots or user churn after a few spends that leads to abandoned accounts which inflate the MAU. For example, an app with only 5,000 downloads may show a MAU in excess of 30,000 due to abandoned accounts. When an app has a higher AUB and excess accounts, it may be rewarded disproportionately more than apps with actual users.

**This leads to some developers getting less kin than they should due to this imbalance.**

While many of the apps have been proactive in controlling this, a minor change in the definition of MAU will also help to address this universally.


## Summary of Improvements
We propose to alter the definition of MAU from:

```python
A user is an MAU in app i if they have spent Kin >= 1 time in app i in the last 30 days.
```
to:
```python
A user is an MAU in app i if they have spent Kin >= 3 times in app i in the last 30 days.
```

The data we have shows that this will keep bot & churn accounts from from being counted as MAU. For the payout calculated on April 11 2021, the MAU and AUB cap would be as follows:

|App|MAU = 1 spend|AUB cap (100,000 * MAU)|MAU >= 3 spends|AUB cap (100,000 * MAU)|
|------------------|-------------|-----------------------|---------------|-----------------------|
|QG32              |948          |94,800,000             |541            |54,100,000             |
|pgbv              |825          |82,500,000             |432            |43,200,000             |
|lsff              |122          |12,200,000             |98             |9,800,000              |
|l83h              |501,610      |50,161,000,000         |132,416        |13,241,600,000         |
|lipz              |55,981       |5,598,100,000          |7,302          |730,200,000            |
|p365              |512,236      |51,223,600,000         |180,502        |18,050,200,000         |
|t1B5              |78,946       |7,894,600,000          |72,282         |7,228,200,000          |
|xnXb              |233,507      |23,350,700,000         |55,727         |5,572,700,000          |

This method is more fair and will ensure rewards count towards users who are engaged in the ecosystem, and will help minimize the effect of bots on rewards.

This will also only affect apps with both large kin deposits and churn or bot accounts. The effect will be to ensure only actual active users are counted towards the reward.

## Implementation
We propose this is included in the KRE as soon as it is approved by the Kin Foundation so it can be part of KRE 3 by April 30 2021


