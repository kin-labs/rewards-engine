
KRE Transaction Guidelines Violation Procedure

# Background

The purpose of this document is to document the process that is taken when a developer is suspected of violating the KRE Transaction Guidelines. This will inevitably make the process more fair, consistent and efficient for all parties involved.

# Responsibilities

## The Kin Foundation

Kin Foundation's role is to maintain a fair playing field for developers across the ecosystem and ensure a safe user experience for all.

## Developers

Developers are required to ensure their apps follow [transaction guidelines](https://github.com/kinecosystem/rewards-engine/blob/master/current-valid-spend-guidelines.md). Additionally, developers should protect their apps from uncompetitive or malicious behavior arising from bots, such as creating inflated transaction, balance, Active User counts (AU) or other factors to artificially inflate KRE rewards to the detriment of other complying apps.

  

Developers should implement best practices to mitigate such activity such as:

1.  Authenticating users through Captcha or SMS
    
2.  Rewarding unique users post install/ uninstall
    
3.  Using [Safety Net attestation](https://developer.android.com/training/safetynet/attestation) to protect against bots
    

  

Apps having difficulty controlling this behavior may have their AU count throttled for the purposes of KRE payment or may be suspended from the KRE all together.

  

# The Steps Explained

## Step 1 – KRE Report Lodged

Generally, all reports related to KRE violations should be emailed to the KRE Operators ([operations@kin.org](mailto:operations@kin.org)) with accompanying evidence. Alternatively, KRE violations may be posted as a new issue on GitHub. Reports can be filed by anyone in respect of any particular application in the ecosystem.

## Step 2 – Report reviewed by KRE Operators

The KRE operators will provide general oversight over the report and assist in progressing it between the relevant decision makers.

Once a report has been lodged on GitHub, the first task of the KRE operators is to review it to confirm:

-   Is the report clear on which application it is in relation to?
    
-   Does the report specify how the application is breaching the KRE Transaction Guidelines?
    
-   Has plausible evidence supporting the claims made in the report been provided or referenced?
    

If the KRE operators feel that something is missing or requires clarification, then in the first instance further information should be requested from the author.

Then, the KRE operators will need to make a decision on whether there is a 'case to answer'. It is not for the KRE operators to judge the report, rather to decide whether its contents are at least plausible. If there is not a case to answer, then the KRE operators can immediately close the report (See Closing a GitHub Report / Logging Decisions).

This will likely be the case when the report is made on trivial or vexatious grounds. In the event there is a case to answer then proceed to Step 3. The KRE operators should aim to make a decision on the report within five business days of it being lodged.

## Step 3 – Developer Notified / KRE Payments Suspended

Upon the KRE operators determining that there is a case to answer the following items need to be promptly actioned:

1.  The relevant developer must be informed: The KRE operators will send the developer the Initial Notice of Violation Report.  
      
    As part of this notice, the developer is directed to our guidelines and policies and given the opportunity to participate in the process if desired. While all views are welcome, their input is not necessarily required. If they do provide input, every effort should be made by the decision makers to weigh up the developer's point of view against the contents of the report. If the developer's input is that they will fix the application, this decision process should still continue until completed.
    

  

2.  As a precautionary measure, we may withhold all future payments from the KRE in respect of the particular application until a final decision is made in respect of the report.  
      
    Given practically, a report could take up to a month to reach the Kin Foundation board depending on the time it was lodged, suspending KRE payments protects the Kin Foundation and promotes fairness across the ecosystem where it might have continued to make KRE payments for a period of time to an application not entitled to them.  
      
    While developers might be nervous to learn their payments are being withheld, in the event the final decision made is that no breach of the guidelines has occurred or no action is to be taken then these withheld payments will be released in full back to the developer. The mechanics to release these KRE payments back to the developer is detailed at:  Implementing a Decision
    

Note that in certain instances the case is fast-tracked directly from Step 3 to Step 4. Specifically, if we have definitive evidence that the KRE Transaction Guidelines were breached via one of the following means the report will be directly passed to the Kin Foundation for decision:

● Developer has breached Kin Foundation Developer Terms (e.g. the application is in breach of applicable laws or contains restricted features or functionality);

● Developer has admitted guilt;

● the Application triggers the KRE operator anti-fraud alerts;

  

## Step 4 – Decision by Kin Foundation

At the earliest opportunity following the original creation of the report, the Kin Foundation reviews the report and any additional information and recommendations provided by the KRE operators. After discussing the relevant details of the case the Kin Foundation votes on whether the report has been substantiated.

  

If the report is determined not to be substantiated, the Kin Foundation pays all withheld Kin and the report is closed. If the report is determined to be substantiated, the developer will be notified of the decision via email and any unpaid KRE payments will be moved to the KRE Carryover Pool for payment in the rest of the calendar year. The Kin Foundation may provide steps to the developer to remedy the infraction in order to receive future payments. The Kin Foundation reserves the right to pay the developer all or part of the withheld funds in the case of minor infractions.

# Closing a GitHub Report / Logging Decisions

### Closing a Report

The developer will be notified via email and the report on Github (if posted there) will also be closed.

### Logging Decision

Every report whether action was taken in respect of it or not needs to be logged at the time the report is closed.

We maintain a log of every report dealt with (whether action is taken or not), this is so we can:

-   monitor grievances and identify product issues and improve our guidelines; - ensure new decisions we make are consistent with previous decisions;
    
-   ensure we are managing developers fairly and equally in our processes.
    

The KRE operator must make a log entry on closing the GitHub report. Please ensure reasonable detail is included.

### Implementing a Decision

#### Withheld KRE payments – Releasing back to the Developer

Any withheld Kin will be paid back to the developer during the next KRE Payment cycle.

#### Withheld KRE Payments – Not releasing back to the Developer

The withheld payments will be added to the KRE Carryover Pool for use in the next KRE Payment cycle and forward.

#### Suspension of the Developer from the KRE program

The developer will be notified via email that they have been suspended from the KRE program. The developer may also receive information regarding the length of their suspension, or terms that must be met by the developer in order to be reinstated into the KRE program. No activity from the application will be taken into account for the purposes of the KRE while suspended.

#### Permanent Ban of the Developer from the KRE Program

The developer will be notified via email that they have been permanently banned from the KRE program. No activity from the application will be taken into account for the purposes of the KRE while banned.
