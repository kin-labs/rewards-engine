
<![endif]-->

# KRE Valid Transaction Guidelines 2.0

These Kin Rewards Engine Valid Transaction Guidelines (the "**KRE Transaction Guidelines**") are supplemental and subject to the [Kin Foundation Developer Guidelines](https://www.kin.org/developers/guidelines.pdf) (the "**Guidelines**"). Unless otherwise defined below, terms defined in the Guidelines have the same meaning when used in these KRE Transaction Guidelines.

*[***Asparagusm*** comment: This should be referred to so it's clear these valid transaction guidelines are not a separate agreement with the Developer in their own right. Additionally please keep in mind that under the official Guidelines, the KF may exclude Developers from KRE payments at their discretion whether or not they have breached these guidelines. This should be enforced as soon as exploits are discovered.  It is good practice to keep the terminology consistent across the ecosystem so definitions have been carried across save having to define key terms again. The terminology used in Version 1.0 of this document was inconsistent with itself and with other documents]*

***Who is this guideline for?***

This guideline outlines the minimum requirements for a Developer to receive a payout from the KRE.  [*link to medium articles that explain context].

1. **Definitions**

The following definitions apply in this document:

| Term | Definition |
| ------------- | ------------- |
| "***Earn Transaction***" |a Transaction originated by you to a User within your Application;  |
| "***P2P***" |a Transaction between one User and another User within your Application;  |
| "***Prohibited Transaction***" | means any Transaction described in '*Section D – Prohibited Transactions*';  |
| "***Spend Transaction***" | a Transaction originated from a User to you within your Application;  |
| "***Subscription***" | an arrangement made between a User and (a) you; or (b) with another User within your Application, to receive something by advance payment; |
|  "***Transaction***"| an instance where KIN is transferred from one wallet to another wallet within the Kin Ecosystem;|
|  "***User***"| an End-User that is a natural person with a single wallet in your Application;  |
| "***you", "your***" | the Developer, and where the context requires, their Application.  |

2. **Eligibility to receive a KRE Payout**

To receive a payout from the KRE you must satisfy in our discretion all of the Minimum Requirements as set out in Section A and all of the applicable Specific Transaction Requirements as set out in Section B.

**SECTION A - MINIMUM REQUIREMENTS**

3. **User to be aware and in control**

3.1. The User must have control over the initiation of the Transaction; and

3.2. The User must, at the time the Transaction occurs, be aware of that Transaction.

*[***Asparagusm*** comment: I've added 'at the time the transaction occurs'.  This prevents for instance, a user who downloads an app for the first time receiving a one-time pop that these transactions will continually occur in the background i.e. Psiphon]*

4. **Developer to be in compliance**

4.1. You must not in our reasonable opinion be:

(a) in breach of the Guidelines and/or these KRE Transaction Guidelines; or

(b) in breach of any app store policy that your Application is subject to the extent we consider this breach to be or likely to be detrimental to the Kin Ecosystem.

*[***Asparagusm*** comment: There should be no expectation from the Developer to receive KRE rewards where the Developer is in breach of the guidelines or their activity otherwise threatens KIN's relationship with Apple or Google.  The KF should not be drawn into disputing whether or not a breach has occurred, it is only necessary the KF have a 'reasonable opinion' it has. Factually it is immaterial.]*

5. **Publicly known entity**

Your Application must be publicly available.

*[***Asparagusm*** comment: This was the transparency clause.  It belongs here]*

6. **Usability**

For each Transaction initiated by a User, the KIN logo must be present on the action/button.

*[**Asparagusm** comment: This is straight from 1.0 however it would be better to say the Application is in compliance with whatever UI policy you have issued].*

**SECTION B - SPECIFIC TRANSACTION REQUIREMENTS**

7.  **Peer-to-Peer (P2P) transactions**

7.1. Each P2P Transaction must include:

(a) clear communication to the User of the amount of the Transaction;

(b) a single tap by the User must result in a clear communication to that User that the Transaction occurred / payment was made.

\(c\) Only 1 KIN can be spent per tap (i.e. like/heart/ok).

(d) The User must have the ability to acknowledge and dismiss this communication.  Once acknowledged, there should be no need to re-communicate this communication with the User.

7.2. If a P2P Transaction is for more than 1 KIN:

(a) the amount of KIN must be clearly stated on or near the action/button; and

(b) the Transaction must have a flow with a minimum of 2 clicks (e.g. undo, confirm, user input amount or amount selection).

8. **Spend transactions**

8.1. Each Spend Transaction, regardless of the amount transacted, must include:

(a) clear communication to the User of the amount of the Transaction;

(b) clear communication to the User of what they will receive in return for their KIN;

\(c\) the Transaction is generated by a unique action undertaken by the User; and

(d) a button where the User is required to tap confirm/acknowledge.

8.2.  A Spend Transaction must not be a Prohibited Transaction.

9. **Earn transactions**

9.1. Each Earn Transaction, regardless of the amount transacted, must include:

(a) clear communication to the User of the amount of the Transaction; and

\(c\) the Transaction is generated by a unique action undertaken by the User;

9.2.  An Earn Transaction must not be a Prohibited Transaction.

10. **Subscription transactions**

10.1. A User may enter into a Subscription with:

(a) the Application (and the payment Transaction by the User of the Subscription will be treated as a Spend Transaction); or

(b) another User, for example a specific content creator (and the payment Transaction by the User of the Subscription will be treated as a P2P Transaction).

10.2. The entering into a Subscription by a User must be clear and explicit to the User and it must contain the following:

(a) How much KIN will be charged in total for the length of the Subscription period;

(b) The length of the Subscription period;

(c\) What the User is to receive as a subscriber;

(d) A confirm/acknowledgement button; and

(e) Information on how to unsubscribe.

10.3. The cost of the Subscription must be set to a fixed amount for the period of the Subscription.

10.4. The length of a Subscription period may only be daily, weekly, monthly or annually.  The length of a Subscription must not exceed one year.

10.5 For each Subscription period set out in Column 1 in the table below (a) the User's payment obligations for that Subscription must correspond to Column 2; and (b) unless the Subscription is renewed by the User, the maximum length of the Subscription must be in accordance with Column 3.

| Column 1 (Subscription Period) | Column 2  (How does a User pay for the Subscription) | Column 3  Maximum length of Subscription (unless User elects to renew) |
| ------------- | ------------- | ------------- |
| Daily | The User pays on a daily basis each day. | 30 days |
| Weekly| The User pays on a weekly basis at fixed internals.| 28 days |
| Monthly |  The User pays on a monthly basis at fixed intervals. | 365 days |
| Annually| The Users pay on an annual basis | 365 days |

10.6. If a User is offered a renewal of their Subscription, the renewal must be offered around the time their current Subscription is due to expire. The offer to renew must be clear and explicit to the User and be in accordance with this Section 10.

10.7. Other than the initial payment of the Subscription cost, subsequent payments for the same Subscription during the Subscription period may be passive payments. A passive payment will be counted as a Spend Transaction, or a P2P Transaction, as the case may be, provided that the frequency of the payments does not exceed Column 2 in Section 10.5 for the relevant Subscription period.  The Application should ensure that the User is aware that a passive payment was made by the User in connection with the Subscription.

10.8 A User must be able to unsubscribe from a Subscription at any time without further obligation to pay.

**SECTION C - PROCESS FOR HANDLING VIOLATIONS**

11. **Developer to be excluded from KRE payments**

11.1. If we reasonably believe that your Application is not in compliance with these KRE Transaction Guidelines:

(a) we will provide notice to you that you are not in compliance.  We may additionally provide steps you need to take to remedy the non-compliance however we are not obliged to do so; and

*[**Asparagusm** comment: Do you want a standard form notice that can be emailed to the developer?  If so I suggest we add this as an annexure]*

(b) we may exclude your Application from receiving any payout from the KRE.  If your Application is excluded, the payout available from the KRE will be distributed rateably amongst the remaining participants of the KRE who remain eligible.

12. **Remedying non-compliance**

12.1. If we have determined your Application is not in compliance with these KRE Transaction Guidelines, in order to remedy the non-compliance (if capable of remedy) you must provide an updated version of the Application in each app store it is available evidencing that the Application is no longer in breach of these KRE Transaction Guidelines.

12.2. Any payouts from the KRE the Application may have received during the period the Application was excluded from payouts from the KRE will not be re-credited.

**SECTION D – PROHIBITED TRANSACTIONS**

The following are Prohibited Transactions for the purposes of the KRE.    An Application which contains any Prohibited Transaction will be excluded from payouts from the KRE.

13. a Transaction or series of Transactions where you have credited the User an amount of KIN, only to require the User to repay all or part of the KIN back to you. The User does not have control or is aware over key aspects of the Transaction sequence.  The purpose of the Transaction or series of Transactions appears, in our view, designed to increase the number of Spend Transactions occurring within your Application.
