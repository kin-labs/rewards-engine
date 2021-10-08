
# KRE Valid Transaction Guidelines V3

These Kin Rewards Engine Valid Transaction Guidelines (the "KRE Transaction Guidelines") are supplemental and subject to the [Kin Foundation Developer Guidelines](https://www.kin.org/developers/guidelines.pdf) (the "Guidelines"). Unless otherwise defined below, terms defined in the Guidelines have the same meaning when used in these KRE Transaction Guidelines.

About these guidelines

The Kin Rewards Engine was built to promote a healthy digital ecosystem which maximizes everyone's opportunity for participation and recognition. However in order to keep a fair playing field amongst developers and ensure a safe user experience for end-users, these guidelines set minimum standards that applications must satisfy in order to be eligible for payouts from the Kin Rewards Engine.

Last updated: 24 September 2021

1.  Definitions
    

The following definitions apply in this document:


| Term | Definition |
| ------------- | ------------- |
| "***Earn Transaction***" |a Transaction originated by you to a User within your Application;  |
| "***KRE Rewards***" | payments of KIN from the Kin Rewards Engine;  |
| "***Module***" | a whitelisted module which purchases KIN from external markets;  |
| "***Passive Subscription Payment***" | a Transaction made by a User to pay for a Subscription where the User is not required to actively initiate the Transaction pursuant to Section 9.7;  |
| "***P2P Transaction***" |a Transaction between one User and another User within your Application;  |
| "***Spend Transaction***" | a P2P Transaction or a U2D Transaction;|
| "***Subscription***" | an arrangement made between a User and (a) you; or (b) with another User within your Application, to receive something by advance payment; |
|  "***Transaction***"| an instance where KIN is transferred from one wallet to another wallet within the Kin Ecosystem;|
|  "***U2D Transaction***"| a Transaction originated from a User to you within your Application; |
|  "***User***"| an End-User that is a natural person with a single wallet in your Application;  |
| "***you", "your***" | the Developer, and where the context requires, their Application.  |

2.  Eligibility to receive KRE Rewards
    

To be eligible to receive KRE Rewards the Application must satisfy all of the Section A - General Requirements and all of the applicable Section B - Specific Transaction Requirements.

SECTION A - GENERAL REQUIREMENTS

3.  Awareness and control
    

3.1. For each Spend Transaction, the User must make a voluntary choice to initiate the Spend Transaction unless it is Passive Subscription Payment.

The Spend Transaction is not a voluntary choice of the User if (a) the User is forced to perform it (b) the User is not aware the Spend Transaction is occurring at the time it occurs, or ( c) the User's wallet was debited by the Developer and this was not expressly authorised by the User at the time of the Transaction. Being aware of the action that initiated the Spend Transaction is not the same as being aware of the Spend Transaction itself.

4.  Developer to be in compliance
    

You must not be:

4.1 in breach of the Terms of Use Agreement and/or these KRE Transaction Guidelines; or

4.2 in breach of any App Store policy (howsoever described) that your Application is available to the extent this is detrimental to the Kin Ecosystem,

5.  Publicly known entity
    

The Application must be publicly available.

6.  Usability
    

For each Transaction initiated by a User, the KIN logo must be present on the action/button.

SECTION B - SPECIFIC TRANSACTION REQUIREMENTS

7.  Spend Transactions
    

7.1. Each Spend Transaction must:

(a) include clear communication to the User of the amount of the Spend Transaction;

(b) include clear communication to the User of what they will receive in return for their KIN;

( c) be initiated by a unique action undertaken by the User;

(d) include a clear confirmation to the User once the Spend Transaction has occurred / payment was made;

(e) include the ability to acknowledge and dismiss the confirmation above. Once acknowledged or dismissed, there should be no need to re-communicate the information to the User.

7.2 If the amount of the Spend Transaction is less than or equal to 100 KIN then the Transaction may be initiated by a single tap by the User (such as the User tapping 'like' or a 'heart', or tapping 'ok') provided that you have firstly informed the User the cost of undertaking the relevant action that initiates the Spend Transaction (e.g. by a tutorial, button confirmation or notification).

7.3 If the amount of the Spend Transaction is greater than 100 KIN, then:

(a) the amount of KIN must be clearly stated on or near the action/button that will initiate the Spend Transaction;

(b) the Spend Transaction must have a flow with a minimum of two taps by the User (e.g. undo, confirm, input amount or amount selection); and

(c) a button must be included requiring the User to confirm/acknowledge the initiation of the Spend Transaction.

8.  Earn Transactions
    

8.1. Each Earn Transaction, regardless of the amount transacted, must include:

(a) clear communication to the User of the amount of the Transaction; and

(b) the Transaction is generated by a unique action undertaken by the User.

9.  Subscription Transactions
    

9.1. A User may enter into a Subscription with:

(a) your Application (and each Subscription payment by the User to the Application will be treated as a U2D Transaction); or

(b) another User, for example a specific content creator (and each Subscription payment by the User to the other User will be treated as a P2P Transaction).

9.2. The entering into a Subscription by a User must be clear and explicit to the User and it must contain the following:

(a) the amount of KIN to be charged in total for the length of the Subscription period;

(b) the length of the Subscription period;

(c) what the User is to receive as a subscriber;

(d) a confirm/acknowledgement button; and

(e) information on how to unsubscribe.

9.3. The cost of the Subscription must be set to a fixed amount for the period of the Subscription.

9.4. The length of a Subscription period must not be less than one week.

9.5 For each Subscription period set out in Column 1 in the table below (a) the User's payment obligations for that Subscription must correspond to Column 2; and (b) unless the Subscription is renewed by the User, the maximum length of the Subscription must not exceed the numbers of days prescribed in Column 3 (if any).

| Column 1 (Subscription Period) | Column 2 (How does a User pay for the Subscription period)  |  Column 3 Maximum length of Subscription (unless User elects to renew)  |
| ------------- | ------------- | ------------- |
| Weekly | The User pays once per week at fixed intervals. | No maximum limit |
| Monthly | The User pays once per calendar month at fixed intervals. | No maximum limit |
| Annually | The Users pays once per year. | No maximum limit

9.6. If a User is offered a renewal of their Subscription, the renewal must be offered around the time their current Subscription is due to expire. The offer to renew must be clear and explicit to the User and be in accordance with this Section 9.

9.7. Other than the initial payment of the Subscription cost, subsequent payments for the same Subscription during the Subscription Period may be Passive Subscription Payments. A Passive Subscription Payment does not require the User to actively initiate the Transaction rather it may occur automatically. You still must ensure that the User is made aware that a Passive Subscription Payment was made by the User in connection with the Subscription at the time the payment is made.

9.8 A Passive Subscription Payment will be counted as a U2D Transaction or a P2P Transaction, as the case may be, provided that the frequency of such payments does not exceed Column 2 in Section 9.5 for the relevant Subscription period.

9.9 A User must be able to unsubscribe from a Subscription at any time without further obligation to pay.

SECTION C - PROCESS FOR HANDLING VIOLATIONS

See [handling violations](https://github.com/kinecosystem/rewards-engine/blob/master/KRE%20Transaction%20Guidelines%20Procedure.md) for details
