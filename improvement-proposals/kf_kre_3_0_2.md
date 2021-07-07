#
# **Kin Improvement Proposal**

The purpose of this document is to outline a proposed improvement to the existing KRE algorithm.

_versioning:_

- _3.0.2_

## **Proposed by:**

_The Kin Foundation_

## **Abstract**

KRE 3.0.2 is a minor update that addresses a vulnerability of the KRE to parked addresses that inflate an app&#39;s Active User Balance.

The Active User Balance (AUB) metric is a simplified incentive mechanism that takes into account all of the mechanisms in previous iterations of the KRE. While previous iterations explicitly rewarded holding, buy tracks, peer to peer transactions, transaction volumes and transaction counts, AUB encompases all these metrics.

An app that has a high AUB naturally has users transacting in its ecosystem (Active Users), and users with higher balances tend to spend more inside the app as the same amount of currency competes for the same amount of goods. Apps are incentivized to keep as many of their users as possible transacting in Kin to maintain a high Active User (AU) count.

Apps are also encouraged to experiment with different incentive methods within their app and the [cap placed on the AUB](https://github.com/kinecosystem/rewards-engine/blob/master/accepted/kik_kre_3_0.md#option-ii-active-user-balances) (100,000 \* AU) is intentionally unconstrained for this purpose.

In short, the AUB metric encourages Kin to flow into apps while also requiring that users remain active and transacting with Kin. We propose a method to address a vulnerability described below.

### **Vulnerability**

Consider an app X with 1,000 Active users. This app can have up to 100,000,000 Kin counted by the KRE for its KRE reward.

Suppose the app has addresses with about 10 Kin each:

| Address # | Kin |
| --- | --- |
| 1 | 10 |
| 2 | 10 |
| ... | 10 |
| 1000 | 10 |

It&#39;s total AUB from usage would be 10 \* 1,000 = 10,000 Kin

However, a vulnerability exists where the app could create an address it controls, and deposit a large volume of Kin to increase its AUB.

| Address # | Kin |
| --- | --- |
| 1 | 10 |
| 2 | 10 |
| ... | 10 |
| **1000** | **100,000,000** |

Its total AUB in this case would jump by orders of magnitude, due to the single _parked address_.

While the incentive metric encourages deposits in addition to active users, it is also important that account balances reflect the _typical usage_ of Kin in the app.

### **Typical Usage**

It is possible to mathematically define typical usage in a simple way that ensures apps are not penalized and only outlier parked addresses are filtered out by the KRE. To define typical usage, we must appreciate that some apps may naturally have large balances and others have smaller ones.

These balances also change with time as apps evolve and gain more use cases. Some ways of defining typical usage are described below:

1. Cap the maximum balance that can be counted per account to 1MM Kin:
 As described above, different apps have different balances and use-cases for Kin, so this method would be too constrained.
2. Cap the maximum balance that can be counted to an average of the app&#39;s current Active Users:
 This is slightly less constrained but given that apps can have a large range in balances, this would also affect non parked addresses

Since parked addresses are extreme outliers of an app&#39;s distribution of balances, the KRE can use a simple standard deviation to protect itself from outlier parked accounts.


 <img src="https://i.imgur.com/sBS0jqp.png"  height="400">
This method allows apps to have a healthy distribution of balances without adding constraints and parked addresses on the extreme outside of normal distribution would be affected. The method is formalized below.

## **KRE Logic Update**
 Where payout for app i is defined as follows: [ref](https://github.com/kinecosystem/rewards-engine/blob/master/accepted/kik_kre_3_0.md#option-ii-active-user-balances)

Payout\_i = (AUB\_i / AUB\_total) \* KRE\_total

let AUB\_i = 0
 for each account of app\_i
 AUB\_i = AUB\_i + IF(account \&gt;= 15stdev\_avg THEN avg ELSE account)

Where for a payment period:
 account = the balance of an active user
 avg = average balance of active users
 15stdev\_avg = 15 standard deviations from an app&#39;s AU balance distribution

If an account is found to be an outlier 15 standard deviations away from the norm, the average is applied to its balance instead.

Discussion
 This method only affects extreme outliers of a distribution of wallets. For any wallet to be affected, it would have to have a z-score of 15, making it more than 15 standard deviations from the average, which is extremely rare.

From a list of 375,062 active user accounts in the considered period (June), only 8 accounts from 4 apps are affected ~ 0.000021%.

While simple, this update helps protect the KRE from parked accounts.

## **Implementation**

We propose this is included in the KRE as soon as it is approved by the Kin Foundation so it can be part of KRE 3 by July 24 2021
