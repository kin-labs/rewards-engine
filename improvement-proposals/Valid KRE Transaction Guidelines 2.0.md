

# KRE Valid Transaction Guidelines 2.0

These Kin Rewards Engine Valid Transaction Guidelines (the "**KRE Transaction Guidelines**") are supplemental and subject to the [Kin Foundation Developer Guidelines](https://www.kin.org/developers/guidelines.pdf) (the "**Guidelines**"). Unless otherwise defined below, terms defined in the Guidelines have the same meaning when used in these KRE Transaction Guidelines. 

*[***Asparagusm*** comment: This should be referred to so it's clear these valid transaction guidelines are not a separate agreement with the Developer in their own right. Additionally please keep in mind that under the official Guidelines, the KF may exclude Developers from KRE payments at their discretion whether or not they have breached these guidelines. This should be enforced as soon as exploits are discovered.  It is good practice to keep the terminology consistent across the ecosystem so definitions have been carried across save having to define key terms again. The terminology used in Version 1.0 of this document was inconsistent with itself and with other documents]*

***Who is this guideline for?***
This guideline outlines the minimum requirements for a Developer to receive a payout from the KRE.  [*link to medium articles that explain context].

1. **Definitions** 

The following definitions apply in this document:

| Term | Definition |
| ------------- | ------------- |
|  "***User***"| an End-User that is a natural person with a single wallet in your Application;  |
| "***P2P***" |a Transaction between one User and another User within your Application;  |
| "***Spend Transaction***" | a Transaction originated from a User to you within your Application;  |
| "***Subscription***" | an arrangement made between a User and (a) you; or (b) with another User within your Application, to receive something by advance payment; |
|  "***Transaction***"| an instance where KIN is transferred from one wallet to another wallet within the Kin Ecosystem;|
| "***you", "your***" | the Developer, and where the context requires, their Application.  |

[***Asparagusm*** comment: Many of the definitions in 1.0 were unnecessary and made the terminology not consistent between clauses]

2. **Eligibility to receive a KRE Payout**

To receive a payout from the KRE you must satisfy in our discretion all of the Minimum Requirements as set out in Section A and all of the applicable Specific Transaction Requirements as set out in Section B.  

**SECTION A - MINIMUM REQUIREMENTS**

3. **User to be aware and in control**

3.1. The User must have control over the initiation of the Transaction; and

3.2. The User must, at the time the Transaction occurs, be aware of that 	Transaction. 

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

9. **Subscription transactions**

9.1. A User may enter into a Subscription with:

(a) the Application (and the payment Transaction by the User of the Subscription will be treated as a Spend Transaction); or

(b) another User, for example a specific content creator (and the payment Transaction by the User of the Subscription will be treated as a P2P Transaction). 

9.2. The day on which payment of the Subscription by the User occurs will be counted as a Daily Active Spender, but any passive payments made by the User during period of the Subscription will not be counted. 

[**Asparagusm** comment:  This is from 1.0 however I do not think it's right.  Please confirm and let's clarify this sentence.]

9.3. The entering into a Subscription by a User must be clear and explicit to the User and it must contain the following:

(a) How much KIN will be charged in total for the length of the Subscription period;

(b) The length of the Subscription period;

(c\) What the User is to receive as a subscriber;

(d) A confirm/acknowledgement button; and

(e) Information on how to unsubscribe.

9.4. The cost of the Subscription must be set to a fixed amount for the period of the Subscription.

9.5. The length of a Subscription period may only be daily (30), weekly (4), monthly (12), or yearly (1).  A Subscription must not exceed one year. 

*[**Asparagusm** comment: To ensure consistency across apps, subscriptions must be in the above intervals up to the maximum prescribed]*

9.6. A User must explicitly elect to renew their Subscription and this must be around the time their current Subscription is due to expire.  An option to renew must comply with section 9.3.

*[**Asparagusm** comment: I've added the renewls are to be dealt with close to the termination of the current subscription period and renewals must follow the same information requirements as starting a subscription]*

9.7. A User must be able to unsubscribe from a Subscription at any time without further obligation to pay. 

*[**Asparagusm** comment: Added no further obligation to pay, so a Developer cannot impose on Users penalty fees or termination fees for unsubscribing early]*

**SECTION C - PROCESS FOR HANDLING VIOLATIONS**

10. **Developer to be excluded from KRE payments**

10.1. If we reasonably believe that your Application is not in compliance with these KRE Transaction Guidelines:

(a) we will provide notice to you that you are not in compliance.    We may additionally provide steps you need to take to remedy the non-compliance however we are not obliged to do so; and

*[**Asparagusm** comment: Do you want a standard form notice that can be emailed to the developer?  If so I suggest we add this as an annexure]*

(b) we may exclude your Application from receiving any payout from the KRE.

11. **Remedying non-compliance** 

11.1. If we have determined your Application is not in compliance with these KRE Transaction Guidelines, in order to remedy the non-compliance (if capable of remedy) you must provide an updated version of the Application in each app store it is available evidencing that the Application is no longer in breach of these KRE Transaction Guidelines.

11.2. Any payouts from the KRE the Application may have received during the period the Application was excluded from payouts from the KRE are forfeited.  Any KIN which is forfeitted pursuant to this section will form part of the KRE's overflow pool.

*[**Asparagusm** comment: I've added that remedying a non-compliance does not entitle to the developer to missed payments.  They will be left in the overflow pool, please confirm]*

----

*[**Asparagusm** comment: Discussion point - Rave

The format of this new document allows us to describe and carve out undesirable behaviours from the guidelines.   We can do this by creating a new concept for example "Excluded Transactions".  Let's discuss if we should add the following at 8.2. to address Rave.

8.2.  A Spend Transaction under section 8.1. must not be an Excluded Transaction:

New definition:

Excluded Transaction means:

(a) a Transaction or series of Transactions where the Application gifts KIN to the User but then immediately requires the User to pay all or part of the gifted KIN back to the Application.

(We can add further limbs to this definition has new behaviours are identified). 
]]]















