
# Report 1 – Automattic Cloudup Privilege Escalation

## Basic Information

Company: Automattic
Report ID: https://hackerone.com/reports/13959
Reported By: niks
Date: May 29, 2014
Weakness: Improper Authentication - Generic
Severity: High (But No Severity given to the report)
Status: Solved

---

## Executive Summary

So basically in this part of the vulnerability we can see that User or any user can just read or write the file that has been uploaded to any server of Cloudup.com can be seen by bypassing the Download parameter of the URL it happens as of no response on the communicated URL or parameters also that are basically accessible even outside of the Box that may cause error sometime. Even if you have set the password for the file in this case still no validation was on the download parameter the File was accessible to attacker.

---

## Attack Scenario


What access does the attacker initially have? 

-> Attacker has access to the files as well as the internal directory structure that can easily be bypassed by parameter even if there is password stacked but not proper authentication mechanism on parameter.

What is the target?

-> The target was [https://cloudup.com](https://cloudup.com/)

What is the objective?

-> As an attacker we can access the files for the different users also an attacker try to look for admin based sensitive files or different files that might contain a lot of detailed information. Even attacker could mark the whole map of the backend server by multiple trails. (The attacker begins as a legitimate low-privileged user with a valid Cloudup account. No elevated privileges are required. By manipulating the file URL, the attacker can access resources owned by another authenticated user)

---

## Root Cause

Why was this vulnerability possible?

It was possible because of the missing authorization headers from the webpage also it was possible because of the missing header based parts.

Was authentication missing?

-> Yes, Authentication was missing in this part especially they properly configured the authentication part on file but forget to put it on parameters.

Was authorization missing?

-> Yes Authorization was seen to be missing in this part if Attacker can access the Victim's file even if it is password protected after manipulating the URL

Was access control incorrectly implemented?

Access control was implemented properly on the file side but on the Parameter side they might have had made that part in form of different header that might helped them prevent those parts

---

## Attack Flow

1. Go to [https://cloudup.com](https://cloudup.com/) and make two accounts say X and Y.

2. login with the account X and upload a file(can be txt,php,anything) and set a password for this file, now right click on download and copy the link location of the file. It is something like ([https://cloudup.com/files/iDQ23wk5p1O/download](https://cloudup.com/files/iDQ23wk5p1O/download))

3. Now logout from account X, and login with account Y. Now load the link location of file copied in step 2. what you will get? Forbidden, right?

4. But wait a second, modify the url mentioned in step 2 like below [https://cloudup.com/files/iDQ23wk5p1O/](https://cloudup.com/files/iDQ23wk5p1O/) (remove the download part)


---

## Security Impact

Confidentiality - This case confidentiality didn't changed

Integrity - But integrity got compromised as someone else was reading my data if further more exploitation would have done might have also edited it too.

Availability - This too failed as attacker was able to access the other user data.

Business Impact - THIS can lead to leak of multiple sensitive information leakage, admin things might have got stolen, internal mapping of the organization would have been mapped.

---

## MITRE ATT&CK Mapping

Technique - https://attack.mitre.org/techniques/T1619/ this technique of Cloud Storage Object Discovery would have been used here that fits mostly in this case.

Why it applies

Adversaries may enumerate objects in cloud storage infrastructure. Adversaries may use this information during automated discovery to shape follow-on behaviors, including requesting all or specific objects from cloud storage. Similar to [File and Directory Discovery](https://attack.mitre.org/techniques/T1083) on a local host, after identifying available storage services (i.e. [Cloud Infrastructure Discovery](https://attack.mitre.org/techniques/T1580)) adversaries may access the contents/objects stored in cloud infrastructure.

---

## Cyber Kill Chain

Recon

Weaponization

Delivery

Exploitation

Installation

C2

Actions on Objectives

---

## Defender Perspective

How could defenders detect this?

Defensive part might use different mechanisms to authenticate with different things like safe headers when listing the files on visible servers

What logs would help?

Logs that might help them would be if this is being exploited other than this basically they can be learnt from parameter based URL.

What security control could prevent this?

Content-Security Headers and strict Header based controls also authorization of header usage can try to prevent this.

---

## Lessons Learned

- The lesson that, I learnt here is try to make it safe with paramets.
- Try To keep CSP on own server even if it is part of server but client side too
- Take client side seriously maybe this attack can lead to this.