# [GRC Incident Review] “Jeremy from Marketing” Darknet Diaries ep. 36 Review One

## Introduction and Context:
Hello everyone! So, this is my first post in this series. I decided to use Jack Rhysider’s DarkNet Diaries episodes and try to write a review on them from the perspective of analyzing real-world breaches and incident response failures. I am a beginner in this, and I hope that others reading this can learn something and also help me by engaging in discussions so that we all can learn and improve together. 

For those who have not watched the episode or podcast, no worries, for I will give a small gist of it. So, what happened was that the company hired a super hacker named Tinker to perform a penetration test and gain access to all the network, systems, etc., within a week. Tinker had used so many techniques to try to exploit any vulnerability, but ultimately, the Blue Team won the war this time. 

I will focus more on the gaps that were exposed, the controls that worked, and then share my thoughts on potential fixes for the gaps mentioned during the documentary, which Tinker pointed out. 

## GRC Failures and Gaps Exposed:
The first one I noticed was when he mentioned managing to get into the IT shack where all the laptops were on that floor, excluding the personal laptops left by other employees in their cubicles. First, there was no camera positioned to look at the door. Next, when he tried to go in, there was a door stopper keeping it open. Lastly, he was able to take three to four trips to haul laptops to his cubicle area. These points show that there was a failure in Physical Access Control, Access Control for Output Devices. The next was when he managed to bypass the MFA by using a social engineering tactic, Vishing, on the employee in accounting. Gaining access to the Citrix account. Fortunately, it did not have anything on it, as it was a standalone account. AT-2 Security Awareness and AT-3 Role-Based Training policy was a failure in this case, as the person Tinker spoke to had read the MFA code to him. There was one point where Tinker was able to crack the password of an account, which was the company name and the year, so failed IA-5 Authenticator Management. Within the thirty laptops he was going through, he found two that were not encrypted, so there was a failure in CM-6 Configuration Settings. I think that was all. 

## Successful Controls (The Blue Team's Strengths):
Of course, some controls worked as the Blue Team had won in this battle. For instance, the Role-Based Access Control was incredibly strong, as apparently the Company's IT team was able to detect suspicious activity when he was using a finance computer to run PowerShell. They had a 12-character password policy, limited remote logins, per-app MFA, and there were even accounts that had him able to crack the password to get into the account, but not have the permission to do anything. 

As I said earlier, there were failures about the encryption on 2 laptops. There was widespread use of disk encryption on corporate and personal laptops, which made it difficult to mount their hard drive. 

## Policy Recommendations:
So based on this review, the company should employ social engineering techniques and drills at least to focus on Vishing and Phishing. As the one from the Accounting Department had fallen for the tactic. It should mandate monthly practical testing that mimics these scenarios to improve human defense efficiency and effectiveness. Another is to ensure the installation of cameras on all restricted areas, as Tinker would have had a tougher time getting all those laptops from the IT shack had there been a camera facing the door.

## Conclusion:
I think that is all from my side. Let me know what you think. Whether to discuss further or to correct me on this review.
