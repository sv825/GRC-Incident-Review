# Policy Recommendations and Remediation Plan
## GRC Incident Review Series - Chapter One: Darknet Diaries EP: 36 "Jeremy from Marketing"
_Date: October 31, 2025; Author: Sreya Vavilala_

## I. Executive Summary
This document focuses on the remediation strategies and policy approaches required for the comprehensive security control gap analysis done on the penetration testing scenario discussed in Jack Rhysider's Darknet Diaries episode 36 "Jeremy from Marketing". From the incident exposed, the Physical Access Control, Security Awareness Training, and some foundational Authenticator Management weaknesses were exposed. 

However, it should be noted that the Blue Team demonstrated a high degree of defense in several areas such as strong passphrase requirements, full disck encrypttion on users' devices, strict remote access control (AC-3), and advanced role-based application monitoring (SI-4). These are what allowed them to detect and stop the Red Team attacker, Tinker. 

There were still a few identified failures that necessitate the immediate, mandatory updates to corporate security policies to close the human and configuration-level exploitable areas. 

## II. Scope and Methodology
**Scope:** It addresses the deficiencies related to physical security, privileged access management, user training, and information system component configuration.

**Methodology:** The NIST Special Publication 800-53 Revision 5, NIST Special Publication 800-63 Revision 3, and Jack Rhysider's podcast episode were utilized to map observed incident failures to specific controls

## III. Identified Policy Gaps and Root Cause Analysis
The following critical policy gaps and corresponding NIST SP 800-53 controls were compromised during the penetration test:

