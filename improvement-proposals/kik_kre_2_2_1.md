# Kin Improvement Proposal
The purpose of this document is to outline a proposed improvement to the existing KRE algorithm. 

*versioning:*
- *2.2.1*

## Proposed by:
*Kik Interactive Inc*

## Abstract
After discussions with the Kin Ads team, the data collection technique described in KRE 2.2 does not adequately support for banner ads. This proposal remedies that issue.

## Summary of Improvements
Using banner ads as a form of advertisement creates a unique challenge for data collection. At the time a banner ad is view, developers do not know how much the impression was worth. Moreover, it is unreasonably disruptive to compensate the user at that exact time. In the current description of KRE 2.2 Module Submission, developers are required to label all earns which come from Kin Bought through a module. This is not practical for banner ads. Thus, we recommend:
- Implementers of modules will no longer have to label earns as coming from a module. All earns that happen in an app in a day will be considered applicable earns.
- Module creators will need to pay developers daily (or more frequently) for Kin bought, and label payments accordingly.
- The amount of Kin bought will be the minimum of: the daily amount of Kin earned by users, and the daily amount of Kin Bought via modules. I.e. Kin that is bought through a module and sent to users.

### Buy Track example
In order for the Kin bought calculation to be clear, we recommend adding the following examples to the Buy Track:<br/>
If 100 Kin is bought through a module in app `i` on August 1st, and 200 is earned by users in app `i` on August 1st, `buy_i=100`.<br/>
If 100 Kin is bought through a module in app `i` on August 1st, and 50 is earned by users in app `i` on August 1st, `buy_i=50`.<br/>

### Module Submission

The following will replace the Module Submission section proposed in KRE 2.2:

In order for a submitted module to be recognized for use in the Buy Track it must be demonstrated that user actions resulted in the purchase of Kin. Blockchain transactions must occur for each user earn that happens through the module demonstrating:
- That the user received Kin in exchange for a Kin purchase taking place
- Which digital service (app) the purchase was made through
- Which submitted Buy Track module was used

Specifically, a *mod_id* must be appended to the memo field for daily (or more frequent) Kin payments to developers for purcahses. A *mod_id* is a 4-digit module identifier for the Buy Track module (i.e. *kads*)

The payment transactions from modules to developers must start with the form:
- *1-mod_id-app_id* i.e. *1-kads-lipz*


In addition, the Buy Track module submission must contain additional information as to how it can be audited by KRE Operators or other parties. In addition to the above, developers must fill out this [form](https://docs.google.com/forms/d/e/1FAIpQLSf5h20erxuLMTFIWwqQxLynLyQV-UYXXMgOaamRArPxzL9afQ/viewform?usp=sf_link) which must be approved by the Kin Foundation prior to counting towards the KRE. In order for the submission to approved:
- It must be verifiable that the amount of Kin claimed to be sent to users through the module is no more than the amount of Kin sent to the developer from the module creator.
- The user either watched an advertisement, filled out a survey or paid in another currency for the Kin before Kin was sent to the user.
- The user is paid Kin at a rate at most 3x the market rate (i.e. a user can earn at most $0.03 worth of Kin for an ad generating $0.01 of revenue, and a user buying $1.00 worth of kin cannot receive more than $3.00 worth of Kin).

## Implementation
We propose this is included in the KRE as soon as it is approved so it can be part of the KRE 2.2 update on August 1st, 2020.
