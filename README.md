# Phishing-Email-Practice-Report
This is report for a phishing email investigation 


Email 1

---------------
Email Artifacts
---------------

Sending Address:QPE77756@mun.ca

Subject Line: Your Amazon.co.uk order of "ION Audio Turntable.."

Recipients:jack.tractive@abcindustries.co.uk

Reply-to:None

Date and Time: 4/19/2017, 12:35 PM

Sending Server IP (Sanitized): 68[.]114[.]190[.]29

Reverse DNS: mtaout004-public.msg.strl.va.charter.net

-------------
Web Artifacts
-------------

Full URL (Sanitized): hxxp://id820update.refundsys59.co.uk/invoice103amz/index.php?email=jack.tractive@abcindustries.co.uk

Root Domain: None 

What Analysis have you done? (URL2PNG, WannaBrowser, VirusTotal, URLScan.io, etc)

*The styling for the email is super simple, which is a dead giveaway for a malicious email, Amazon and other reputable companies usually have very professional styling. It also has an autoconfirm email address, which could me a credential harvester of sorts. After collecting all of the email artifacts, I plugged the IP address I found in Sublime into Who is and discovered more information, such as the time and that there is no reply to address. Performed a URL Scan, screenshot shows nothing, so that means that it isn't a domain that was compromised . Only one flag on Virus Total went off for Webroot, the initial email should be harmless, unless the user enters in their information. 

***Defensive Measures 


What defensive measures do you want to take?

I would simply block the sending email address, since it doesn't appear to be coming from a URL the company benefits from.




Email 3

---------------
Email Artifacts
---------------

Sending Address: FSDFAS2423N23K@gmail.com

Subject Line: COVID19 - GET TESTED NOW!

Recipients: matthew.beaman@abcindustries.co.uk

Reply-to:None

Date and Time: Fri, 12 Jun 2020 21:23:00 +0100

Sending Server IP  (Sanitized): 209[.]85[.]160[.]173

Reverse DNS: mail-qt1-f173.google.com

--------------
File Artifacts
--------------

File Name: COVID19-Testing-Kit-2020.pdf.exe

SHA256 Hash:8B2E701E91101955C73865589A4C72999AEABC11043F712E05FDB1C17C4AB19A


What Analysis have you done? (URL2PNG, WannaBrowser, VirusTotal, URLScan.io, etc)

*The styling for the email is very simple and is asking us to open an attachment to claim a COVID testing kit, which already does not seem right, usually it would be a link of some sort. It is trying to make us hurry up and act by stating that "if you do not act soon, we will give your slot to someone else. This is straight forward that it will try to run malicious software on our machine if we run this (in a normal scenario). With the SHA256 hash, I plugged it into virus total and 60 flags are going off, this file is definitely malicious. I also put in file hash into Cisco Talos reputation check and it was also ringing as malicious and is a backdoor trojan. According to the MITRE ATT&CK TTP, this is an executable that is attempting to gain persistence and elevate itself and also perform lateral movement on the victim network by gaining credentials and exfiltrate this information back to the Command & Control server.

***Defensive Measures 


What defensive measures do you want to take?

I would set rules on the firewall and IPS to block the SHA256,MD5 hash(If it was available). We cannot simply block the domain since it is coming from a google email gateway and we do not want to block legit emails. I would also block that specific email address, since it does not benefit the business, nor do we need emails from it. 



