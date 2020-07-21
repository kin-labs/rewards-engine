# Kin Improvement Proposal
The purpose of this document is to outline a proposed improvement to the existing KRE algorithm. 

*versioning:*
- *2.2.1*

## Proposed by:
*Kik Interactive Inc*

## Abstract
KRE 2.2 is an update which more specifically rewards developers for getting users to buy Kin. It simplified the KRE Buy Track and takes effect August 1st, 2020. After integration discussions with the Kin Ads team, the data collection technique described in KRE 2.2 does not adequately support passive ad products like banner ads. Moreover, Kin Ads (and future modules) may not be able to pay Kin to developers in real or semi-real time. The following proposal increases the flexibility of the KRE 2.2 Buy Track and clarifies definitions of Kin Bought to accommodate these issues.

## Summary of Improvements
Using passive ad types such as banners  creates a unique challenge for data collection. At the time a banner ad is viewed, developers do not know how much the impression was worth. Given that, it is challenging to compensate the user at that exact time. In the current description of KRE 2.2 Module Submission, developers are required to label all earns that come from Kin Bought through a module. This is not practical for banner ads. To mitigate these challenges, we recommend the following adjustments to KRE 2.2:
- Developers who implement a module will no longer have to label earns as coming from a module. All earns that happen in an app in a day will be considered applicable earns.
- Module creators should pay developers daily (or more frequently) for Kin bought, and must label payments accordingly. Kin that is sent to developers in multi-day batches will have been considered to have been purchased on the same day, and may thus negatively impact KRE payouts for that developer if KRE payout caps are met.
- Note that the amount of Kin bought via modules on a certain day will be the amount of Kin sent to developers from approved modules on that day (regardless of when the user action took place that resulted in a subsequent  purchase of Kin). i.e. If a user watches an ad on August 1st, 2020, and the developer is paid for that ad completion by the module creator on September 1st, 2020 the Kin will have been considered bought on September 1st, 2020.
- The `buy_i` value used in payout calculations (the amount purchased and sent to users) will be the minimum of: the daily amount of Kin earned by users, and the daily amount of Kin Bought via modules: i.e. Kin that is bought through a module and sent to users.

Note that while the impetus for this change was related to banner ads, all forms of advertising revenue will count towards the Buy Track (i.e. interstitial ads, offer walls, etc.)

### Impermissible Kin Bought
To keep the playing field fair for all developers we propose the following rule that will calibrate the starting point of KRE 2.2:
Any Kin purchased due to user actions before August 1st, 2020 will not be considered part of Buy Track from August 1st, 2020 and forward. i.e. if a user watches an ad on July 1st, 2020 and the developer is paid by the module creator on August 1st, 2020, this Kin will not count towards the Buy Track.

### Buy Track example
For the Kin bought calculation to be clear, we recommend adding the following examples to the Buy Track:<br/>
If 100 Kin is bought through a module (i.e. sent to the developer from a module) in app `i` on August 1st, and 200 is earned by users in app `i` on August 1st, `buy_i=100`.<br/>
If 100 Kin is bought through a module (i.e. sent to the developer from a module) in app `i` on August 1st, and 50 is earned by users in app `i` on August 1st, `buy_i=50`.<br/>

### Module Submission

The following will replace the Module Submission section proposed in KRE 2.2:

For a submitted module to be recognized for use in the Buy Track it must be demonstrated that user actions resulted in the purchase of Kin. Blockchain transactions must occur for each user earn that happens through the module demonstrating:
- That the user received Kin in exchange for a Kin purchase taking place
- Which digital service (app) the purchase was made through
- Which submitted Buy Track module was used

Specifically, a *mod_id* must be appended to the memo field for daily (or more frequent) Kin payments to developers for purchases. A *mod_id* is a 4-digit module identifier for the Buy Track module (i.e. *kads*)

The payment transactions from modules to developers must start with the form:
- *1-mod_id-app_id* i.e. *1-kads-lipz*


In addition, the Buy Track module submission must contain information denoting how it can be audited by KRE Operators or other parties. Developers must complete this [form](https://docs.google.com/forms/d/e/1FAIpQLSf5h20erxuLMTFIWwqQxLynLyQV-UYXXMgOaamRArPxzL9afQ/viewform?usp=sf_link) which must be approved by the Kin Foundation prior to counting towards the KRE. In order for the submission to approved:
- The user either watched an advertisement, filled out a survey or paid in another currency for the Kin before Kin was sent to the developer.
- The user/developer are paid Kin at a rate at most 3x the market rate (i.e. a user can earn the developer at most $0.03 worth of Kin for an ad generating $0.01 of revenue, and a user buying $1.00 worth of kin cannot receive more than $3.00 worth of Kin).

### Alternative Option: Monthly payments
As an alternative to daily (or more frequent) payments from developers we also considered aggregating payouts monthly. In this case, module developers would still be required to abide by everything set out in the Module Submission section above. However, making large batch payments for a month's worth of purchases will no longer negatively impact KRE payouts to developers. Specifically, the KRE would aggregate all Kin sent to developers from Modules from the `Month_x` 10th, 2020 to `Month_(x+1)` 9th inclusive as Kin purchased in `Month_(x-1)`. i.e. any Kin sent to developers from modules between September 10th, 2020 and October 9th, 2020 inclusive would count as Kin Bought in August of 2020. This payment would be made with the next KRE payout happening on or after `Month_(x+1)` 15th (October 15th, 2020 in our example). The logic for payouts of the Buy Track would be changed to the following:

`Let KRE_buy_y be the total amount of Kin paid to developers for the Buy track in month y`<br/>
`Let days_y be the number of days in month y`<br/>
`Let buy_i,y be the total amount of Kin purchased and sent to users through their attention (ads) or fiat currency through a registered whitelisted module in app i in month y`  <br/>

Then the buy payout for app i is:  
`Payout_buy_i,y = min(KRE_buy * buy_i,y / (sum for all apps j buy_j,y), buy_i,y)`

The daily payout descriptions would be adjusted accordingly to show that the Spend and Hold tracks are calculated daily while the Buy Track is calculated separately on a monthly basis.

This method is more fair for module creators: no one will be able to create a module which gets developers paid KRE payouts for August 2020 before October 15th, 2020. This does have a downside though as this fairness comes at the cost of flexibility. Namely, if a module creator can pay developers faster than monthly with a 30-day lag, the developers who implement said module will still not be paid by the KRE at that time. Moreover, the module creator should wait until the 10th of the following month to issue payments to ensure that transactions are counted accordingly.

## Implementation
We propose this is included in the KRE as soon as it is approved so it can be part of the KRE 2.2 update on August 1st, 2020.



