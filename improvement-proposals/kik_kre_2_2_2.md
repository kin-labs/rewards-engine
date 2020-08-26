# Kin Improvement Proposal
The purpose of this document is to outline a proposed improvement to the existing KRE algorithm. 

*versioning:*
- *2.2.2*

## Proposed by:
*Kik Interactive Inc*

## Abstract
This update fixes an incorrect statement in the KRE Valid Transaction Guidelines and aims to streamline the process for letting a module be accepted into the KRE.

## Summary of Improvements
First, we recommend removing 10.2 from the [KRE Valid Transaction Guidelines](https://github.com/kinecosystem/rewards-engine/edit/master/current-valid-spend-guidelines.md). This should have been removed with the introduction of KRE 2.2.1 as it is no longer required by developers.<br/>
*10.2 The total aggregate KIN sent to a User by his/her use of the Module must not be greater than the amount of KIN the Developer received through the Module for the equivalent operation.*


Second, we recommend streamlining the process for new Buy Track Modules to be approved by the Kin Foundation. Currently, the process can take up to a full month to take place (typically, issues are voted on by the board at the monthly Foundation meetings). A month is a long time for a developer to wait to enter the buy track of the KRE. We propose that modules be default accepted *under review* during the interim period between which they have had their sign up form accepted by KRE Operators, and before the Kin Foundation has the chance to view the module's submission. The relevant section to be updated is below:

**Module Submission**

*Existing:* The Buy Track module submission must contain information denoting how it can be audited by KRE Operators or other parties. Developers must complete this [form](https://docs.google.com/forms/d/e/1FAIpQLSf5h20erxuLMTFIWwqQxLynLyQV-UYXXMgOaamRArPxzL9afQ/viewform?usp=sf_link) which must be approved by the Kin Foundation prior to counting towards the KRE.

*Proposed:* The Buy Track module submission must contain information denoting how it can be audited by KRE Operators or other parties. Developers must complete this [form](https://docs.google.com/forms/d/e/1FAIpQLSf5h20erxuLMTFIWwqQxLynLyQV-UYXXMgOaamRArPxzL9afQ/viewform?usp=sf_link). The module must first be approved by KRE operators for form completeness. After this, the module will be considered *under review* until it is fully approved by the Kin Foundation. While under review, the module will still be used to calculate KRE payouts but the Kin Foundation reserves the right to halt KRE payments for the module's use at any time. Moreover, regardless of a module's probation status, anyone can submit a report of a violation via the [KRE Transaction Guidelines Violation Procedure](https://github.com/kinecosystem/rewards-engine/blob/master/KRE%20Transaction%20Guidelines%20Procedure.pdf).

## Implementation
We propose this is included in the KRE as soon as it is approved.
