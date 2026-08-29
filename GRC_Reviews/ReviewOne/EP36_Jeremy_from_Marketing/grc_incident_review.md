# [GRC Incident Review] "Jeremy from Marketing" — Darknet Diaries EP. 36

Date: October 31, 2025 | Author: Sreya Vavilala

*Edited and revised August 28, 2026*

## Introduction and Context

This is the first post in the series. I'm using Jack Rhysider's Darknet Diaries episodes to write reviews from the perspective of analyzing real-world breaches and incident response failures. If you work in this space and see something I've missed or gotten wrong, I want to hear it.

For anyone who hasn't heard the episode: a company hired a penetration tester, Tinker, to gain access to their network and systems within a week. He used a wide range of techniques to find an exploitable path, and the Blue Team held.

I'll focus on the gaps that were exposed, the controls that worked, and what I'd recommend to close the gaps.

## GRC Failures and Gaps Exposed

The first was the IT shack, where the laptops on that floor were stored, not counting the personal laptops employees left in their cubicles. No camera was positioned on the door. A door stopper was holding it open. Tinker made three or four trips hauling laptops back to his cubicle. That's a failure of **PE-3 Physical Access Control** and **PE-16 Delivery and Removal**, since equipment left the controlled area with no authorization or record.

Next, he bypassed MFA through vishing, calling an employee in accounting who read the passcode back to him. That gave him the Citrix account, which turned out to be standalone with nothing on it. This is a failure of **AT-2 Literacy Training and Awareness** and **AT-3 Role-Based Training**.

He also cracked a password that was the company name plus the year, which fails **IA-5 Authenticator Management**.

Out of roughly thirty laptops he went through, two were unencrypted. That's **SC-28 Protection of Information at Rest**, with **CM-6 Configuration Settings** as the underlying cause, since those machines had drifted from the secure baseline.

## Successful Controls (The Blue Team's Strengths)

Several controls held, which is why the Blue Team won.

Monitoring worked. The IT team flagged suspicious activity when he ran PowerShell from a finance computer, which is **SI-4 System Monitoring** doing its job.

Access control worked separately from that. There were accounts where he cracked the password, got in, and then couldn't do anything with the access, because permissions were scoped to the role. That's **AC-3 Access Enforcement** and RBAC working as designed.

They also had a 12-character password policy, limited remote logins, and per-app MFA.

Disk encryption was widespread on both corporate and personal laptops, which made mounting the drives difficult. The two unencrypted machines were the exception, not the norm.

## Policy Recommendations

Run social engineering drills focused on vishing and phishing, monthly and unannounced. The accounting employee fell for a live call, and the only way to build resistance to that is repeated practice against realistic scenarios.

Install cameras covering all restricted areas. Tinker would have had a much harder time removing laptops from the IT shack with a camera on the door.

The full remediation plan, with control mappings, root cause analysis, and a phased implementation schedule, is in [POLICY_RECOMMENDATIONS.md](POLICY_RECOMMENDATIONS.md).

## Conclusion

That's my read. If you see it differently or think I've mapped a control wrong, tell me.
