# Policy Recommendations and Remediation Plan
## GRC Incident Review Series — Review One: Darknet Diaries EP. 36 "Jeremy from Marketing"

_Date: October 31, 2025; Author: Sreya Vavilala_

_Edited and revised August 28, 2026_

> **Note:** This review was originally written against NIST SP 800-63 Revision 3, which was superseded by Revision 4 on August 1, 2025. The authenticator recommendations in Section IV have been updated to Revision 4 guidance.

## I. Executive Summary
This document covers the remediation strategies and policy approaches required following a security control gap analysis of the penetration testing scenario discussed in Jack Rhysider's Darknet Diaries episode 36, "Jeremy from Marketing." The incident exposed weaknesses in physical access control, security awareness training, authenticator management, and baseline configuration.

The Blue Team demonstrated a high degree of defense in several areas: strong passphrase requirements, full disk encryption on user devices, restricted remote access (AC-17), role-based access enforcement (AC-3), and application monitoring (SI-4). These are what allowed them to detect and stop the Red Team attacker, Tinker.

The failures below require mandatory updates to corporate security policy to close the human and configuration-level exposures.

## II. Scope and Methodology
**Scope:** Deficiencies related to physical security, privileged access management, user training, and information system component configuration.

**Methodology:** NIST SP 800-53 Revision 5, NIST SP 800-63B, and the podcast episode were used to map observed incident failures to specific controls.

## III. Identified Policy Gaps and Root Cause Analysis
The following policy gaps and corresponding NIST SP 800-53 controls were compromised during the penetration test:

| Incident Failure | Affected NIST SP 800-53 Control | Root Cause Analysis |
|---|---|---|
| **Physical Security Breach (IT Shack)** | **PE-3** Physical Access Control, **PE-16** Delivery and Removal (NIST, 2020) | No camera covering the door and no secured entry, compounded by a door stopper holding a restricted room open. Equipment left the controlled area across multiple trips with no authorization and no record. |
| **Vishing / MFA Bypass** | **AT-2** Literacy Training and Awareness, **AT-3** Role-Based Training (NIST, 2020) | No social engineering training covering vishing vectors or MFA protocol boundaries. |
| **Weak Admin Password** | **IA-5** Authenticator Management (NIST, 2020) | Use of publicly known organizational context, the company name and year, despite a strong user password policy elsewhere. |
| **Unencrypted Assets** | **SC-28** Protection of Information at Rest (NIST, 2020) | Inconsistent enforcement of the full disk encryption SOP. Systems were not consistently returned to the secure baseline, allowing two laptops to drift into a vulnerable state while stored. |
| **Unquoted Service Path Exploit** | **CM-6** Configuration Settings, **AC-3** Access Enforcement (NIST, 2020) | The unquoted service path violates the secure baseline configuration requirement. A third-party access control tool's configuration overrode native Windows **Write** permissions, letting the Red Team drop malware into the system directory and gain remote _System Level_ privileges. |

## IV. Formal Policy Recommendations
The following recommendations should be incorporated into the organization's authoritative security policies, SOPs, and employee handbooks.

### 1. Physical Security Enhancements (PE-3, PE-16)
**Policy Statement:** The company should implement layered physical access controls for all restricted areas, including data centers, IT shacks, network closets, and other IT equipment storage rooms.

1. **Mandatory Surveillance:** Install and maintain 24/7 video surveillance positioned to monitor all entry and exit points of restricted areas, including the IT shack. Retain footage for a minimum of 60 days.
2. **Access Integrity (Zero Tolerance):** Using door stoppers to hold security doors open is explicitly forbidden. Any restricted room found with its door propped open triggers an automatic security incident response and mandatory retraining for the responsible department.
3. **Asset Handling SOP:** Implement an authorization process for removing or relocating IT assets from restricted areas, requiring at least one sign-off and a documented inventory record.

### 2. Security Awareness Training Overhaul (AT-2, AT-3)
**Policy Statement:** The company should mandate annual, practical, role-specific security awareness training with particular focus on social engineering tactics and defense.

1. **Mandatory Vishing Simulation Drills:** Conduct monthly unannounced vishing drills across all departments, specifically testing whether employees will share MFA passcodes. Departments that fail must undergo targeted retraining within the week.
2. **MFA Protocol Mandate:** Strictly forbid employees from sharing one-time passcodes or any credential data over phone, email, or unencrypted chat under any circumstance. The policy must state plainly that **IT personnel will never request these codes**.
3. **Workstation Lock Requirement (AC-11):** Require employees to lock their workstations immediately upon leaving their desk, regardless of how long they expect to be away.

### 3. Authenticator Management (IA-5)
**Policy Statement:** The company should enforce strong authenticator requirements for all accounts, including privileged and system-level authenticators, and prohibit the use of organizational context in passwords.

1. **Local Administrator Password Randomization:** Randomize the local administrator password on every workstation, unique per device, so that compromise of one machine does not grant access to others. Passwords must not include the company name, year, or similar context.
2. **Blocklist Enforcement:** Screen all prospective passwords against a blocklist covering known breached credentials, dictionary words, repetitive or sequential characters, and context-specific terms including the company name, current year, and common internal abbreviations. This aligns with NIST SP 800-63B Revision 4.
3. **Length Over Composition:** Set a minimum length of 16 characters for privileged accounts and permit passphrases up to at least 64 characters. Per SP 800-63B Revision 4, do not impose composition rules requiring specific character types, and do not force periodic rotation of user passwords absent evidence of compromise. Length and blocklist screening deliver more resistance than complexity rules, which push users toward predictable substitutions.

### 4. Configuration and Access Control Management (CM-6, SC-28, AC-3)
**Policy Statement:** The company should enforce cryptographic protection for all information at rest and ensure configuration settings, particularly for third-party tools and software, properly enforce least-privilege access and prevent unauthorized command execution.

1. **Mandatory Encryption SOP:** Update the Configuration Management SOP so that all corporate laptops, desktops, and portable storage media have full disk encryption enabled prior to issue.
2. **Third-Party Access Control Review:** Review all third-party software and access control tools to confirm they correctly enforce the least-privilege model, and specifically that administrative rights granted by those tools cannot bypass system security boundaries by granting **Write** access where native Windows denies it.
3. **System Integrity and Monitoring (SI-4, CM-6):** Configure operating system settings to restrict high-risk applications such as PowerShell and command prompt to IT personnel who genuinely require them. Log all attempts to run restricted applications to reduce the attack surface across the wider organization.

## V. Next Steps and Implementation Plan

| **Phase** | **Task** | **Responsible Team** | **Time** |
|---|---|---|---|
| **I. Policy Approval** | Draft the policy revisions and obtain executive sign-off. | Leadership | **0–2 weeks** |
| **II. Technical Remediation** | Install surveillance in all restricted areas. Implement automated FDE compliance checks. Randomize all local administrator passwords, unique per device. | IT Department | **2–4 weeks** |
| **III. Access Control Review** | Review and reconfigure third-party access tools to ensure least privilege is correctly enforced. | IT Department Head | **4–6 weeks** |
| **IV. Training Execution** | Develop updated vishing simulation content, then run a company-wide drill followed by targeted retraining. | IT Department | **4–8 weeks** |
| **V. Audit and Verification** | Audit adherence to the revised policy. Where non-compliance is found, produce a remediation plan within the week for management and leadership review. | Management Review | **3 months** |

## VI. References
National Institute of Standards and Technology. (2020, September). *Security and privacy controls for information systems and organizations* (NIST Special Publication 800-53, Revision 5). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-53r5

National Institute of Standards and Technology. (2025, July). *Digital identity guidelines: Authentication and authenticator management* (NIST Special Publication 800-63B, Revision 4). U.S. Department of Commerce.

Rhysider, J. (Host). (2022, August 11). Jeremy from marketing (No. 36) [Audio podcast episode]. In *Darknet Diaries*.
