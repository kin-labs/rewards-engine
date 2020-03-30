# Kin Improvement Proposal
The purpose of this document is to outline a proposed improvement to the Valid Transaction Guidelines and Introduce KRE Update Guidelines. 

*versioning:*
- *Valid Transaction Guidelines 2.1, KRE Update Guidelines 1.0*

## Proposed by:
*Kik Interactive Inc. with significant contributions and revisions by asparagusm.*

## Abstract
The purpose of this proposal is to introduce more effective policy for policing KRE payouts and KRE proposals. This proposal does not attempt to change the KRE algorithm: an app who is following the Valid Transaction Guidelines should see no change to their KRE payouts. 

First, the proposal tightens existing process for KRE violations and introduces the Kin Community Council as a violations filter for the Kin Foundation. Secondly, this proposal introduces timelines and cadence for new KRE monetary policy so developers can be more confident about design decisions which optimize for the KRE.

## Summary of Improvements

### 1) Valid Transaction Guidelines 2.1 ###

*The text below is to replace SECTION C of the Valid Transaction Guidelines.*

**SECTION C - PROCESS FOR HANDLING VIOLATIONS**

10. **Reporting a breach**

A breach of these KRE Transaction Guidelines can be reported by creating a new issue on Github: https://github.com/kinecosystem/rewards-engine/issues (a "Report"). The title of the report must contain "KRE Violation" as well as the name of the Application. In the report, please reference the specific rule(s) breached along with reasonable evidence.

11. **Decision making process**

11.1. If we reasonably believe that your Application is in breach of these KRE Transaction Guidelines or that there is a case to answer in the Report:

(a) we will provide notice to you; and

(b) we will withhold any payments your Application is due to receive from the KRE while we investigate and until a final decision is made.

11.2 Within 14 days from the date the Report is posted, the Kin Community Council will review the Report and the Application and determine whether the alleged breach of the KRE Transaction Guidelines is substantiated:

(a) if the breach is substantiated: the matter will be referred to the Kin Foundation for the final decision;

(b) if the breach is not substantiated: the Report will be closed. Any payments that were withheld from the Application during this period will be released in full.

11.3 No delay in making a decision, or any Application remedying the breach in the intervening period will act as a waiver or impede the decision making process.

12. **Developer is in violation**

12.1. If we determine that your Application breached the KRE Transaction Guidelines:

(a) we will provide notice to you;

(b) we may suspended your Application from receiving all payments from the KRE (if we are already withholding your payments, you will be deemed to be suspended from the date we began withholding these payments);

(c) we may additionally provide steps you need to take to remedy the breach however we are not obliged to give you the option to remedy the breach

12.2 any payments that would have been paid to you during the period of the suspension will instead be added to the KRE Carryover pool for use in the remainder of the current calendar year.

12.3 Repeated or a serious breach of these KRE Transaction Guidelines may result in your permanent ban from the KRE.

12.4 Any suspension may be instated, lifted or reinstated at our sole discretion and subject to any conditions we see fit.

13 **Remedying a breach**
If you have breached these KRE Transaction Guidelines:

13.1 we may permit you to remedy the breach where it is capable of remedy by providing an updated version of the Application in each app store it is available evidencing that the Application is no longer in breach of these KRE Transaction Guidelines;

13.2 any payouts from the KRE that the Application would have received during the period the Application was suspended from payouts will not be re-credited.

### 2) KRE Update Guidelines 1.0 ###

Central banks like the Bank of Canada and the U.S. Federal Reserve System have adopted preset dates for interest rate changes. It is believed that these preset dates lead to better monetary policy. The KRE similarly, should adopt a preset cadence for algorithmic changes. This will allow developers to feel more confident in their application design decisions.

In order for a change to the KRE to be taken from ideation to implementation it must be: publicly posted to Github, the community must have time to weigh in, it must be approved by the Kin Foundation, the community must be notified, and finally the update must be coded.

The Kin Foundation should reserve the right to make changes to the KRE as necessary in extreme circumstances. These changes should be limited to: closing necessary loopholes that go against the spirit of the KRE, correcting other small errors with minimal monetary impact, and fixing larger issues in the case of emergency.

Other than the aforementioned emergency fixes, we propose the following deadlines for various stages of the KRE update process:
*Note that these are placeholder dates and will be updated in a subsequent commit after discussion with the KF*

| Update   | Proposal Draft Deadline | Proposal Final Deadline | Kin Foundation Vote | Date Changes Take Effect |
|----------|-------------------------|-------------------------|---------------------|---------------------|
| Q3 2020  | June 15, 2020 | June 22, 2020 | June 25, 2020| July 1, 2020 |
| Q4 2020  | September 15, 2020 | September 22, 2020 | September 25, 2020| October 1, 2020 |
| Q1 2021  | December 5, 2020 | December 12, 2020 | December 15, 2020| January 1, 2021 |

## Implementation
We propose that this change happens immediately pending approval from the Kin Foundation.
