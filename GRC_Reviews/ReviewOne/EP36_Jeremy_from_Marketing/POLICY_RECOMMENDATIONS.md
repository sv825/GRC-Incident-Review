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
| Incident Failure | Affected NIST SP 800-53 Control | Root Cause Analysis |
|------------------|---------------------------------|---------------------|
|**Physical Security Breach (IT Shack)** |**PE-3** Physical Access Control (NIST, 2020a) | Failed to implement physical security such as cameras and secured doors, and severe user diligence as there was a door stopper in a restricted area. |
|**Vishing/MFA Bypass** |**AT-2** Security Awareness Training, **AT-3** Role-Based Training (NIST, 2020a) | There was a lack of awareness of social engineering training focused on Vishing vectors and MFA protocol boundaries|
|**Weak Admin Password** |**IA-5** Authenticator Management (NIST, 2020a)| There was use of publicly known organizational context, such as the company name and year even with a strong user password policy in place.|
|**Unencrypted Assets** |**SC-28** Protecting of information at rest  to encrypt sensitive data when it is stored (NIST, 2020a)| There is an inconsistent enforcement of the Full Disk Encryption Standard Operating Procedures; The systems were not consistently managed back to the secure baseline. This allowed two laptops to "drift" into an vulnerable state while being stored.|
|**Unquoted Service Path Exploit**|**CM-6** Configuration Settings, **AC-3** Access Enforcement (NIST, 2020a)| The failure to properly quote service path directly violates the requirement for secure baseline configuration; the policy was weakened by the Third-party access control tool as it's configuration overrode the Native Windows **Write** access permissions allowing the Red Team the ability to drop his malware into the system directory, enabling him to gain remote _System Level_ privileges.|

## IV. Formal Policy Recommendations
The following recommendations must be incorporated into the organizations's authoritative security policies, SOPs, and employee handbooks.
### I. Physical Security Enhancements (PE-3)
**Policy Statement:** The company should implement layered physical access controls for all restricted areas, including data centers, IT shacks, network closets, and other IT euipment storage rooms.<br>
      1.**Mandatory Surveillance:** Install and maintain 24/7 video surveillance positioned to monitor all entry and exit points of restricted areas (i.e. IT Shack). Retain all footage for a minimum of 60 days.<br>
      2.**Access Integrity (Zero Tolerance):** Placing door stoppers to keep security doors of any type open is explicitly forbidden. Any door to an unauthorized or restricted room found to be open should trigger an automatic security incident response and mandatory retraining for the responsible department. <br>
      3. **Asset Handling SOP:** Implement an audit proccess on removing or moving the IT assets from restrictetd areas which also require one or more person sign-office and a documented inventory done.

### II. Security Awareness Training Overhaul (AT-2, AT-3)
**Policy Statement:** <br>
      1. **Mandatory Vishing Simulation Drills:** <br>
      2. **MFA Protocol Mandate:** <br>
      3. **Remote Access Diligence (AU-6):** <br>

### III. Authenticator Management (IA-5)
**Policy Statement:** <br>
      1. **Local Administrator Password Rotation:** <br>
      2. **Banned List Enforcement:** <br>
      3. **Complexity Requirements:** <br>

### IV. Configuration & Access Control Management (CM-6, SC-28, AC-3)
**Policy Statement:** <br>
      1. **Mandatory Encryption SOP:** <br>
      2. **Third-Party Access Control Review:** <br>
      3. **System Integrity & Monitoring (SI-4, CM-6):** <br>

## V. Next Steps & Implementation Plan
|**Phase**| **Task** | **Responsible Team** | **Deadline**|
|---------------------|---------------------|---------------------|---------------------|
|**I. Policy Approval**|                     |           |          |
|**II. Technical Remediation**| | | |
|**III. Access Control Review**| | | |
|**IV. Training Execution**| | | |
|**V. Audit & Verification**| | | |






## VI. References
Rhysider, J. (Host). (2022, August 11). Jeremy from Marketing (Episode 36) [Audio podcast - YouTube]. Darknet Diaries.

National Institute of Standards and Technology. (2020a, September). Security and Privacy Controls for Information Systems and Organizations (NIST Special Publication 800-53, Revision 5). U.S. Department of Commerce.

National Institute of Standards and Technology. (2020b, June). Digital Identity Guidelines: Authentication and Lifecycle Management (NIST Special Publication 800-63B, Revision 3). U.S. Department of Commerce.
