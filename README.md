# SOC120---Phishing-Mail-Detected---Internal-to-Internal

## Objective

In this investigation, I was alerted that there was a Phishing Mail detected from two internal users. I need to identify the indicators of compromise and assess whether the phishing mail is a  true positive  malicious threat to users.


## 📌 Alert Overview

EventID: 52
Event Time: Feb 07, 2021, 04:24 AM
Rule: SOC120 - Phishing Mail Detected - Internal to Internal
Level: Security Analyst
SMTP Address: 172.16.20.3
Source Address: john@letsdefend.io
Destination Address: susie@letsdefend.io
E-mail Subject: Meeting
Device Action: Allowed

<img width="1842" height="524" alt="image" src="https://github.com/user-attachments/assets/1cc330e2-d2a9-4738-a2b8-2639914d41aa" />



## 📝 Initial Information


From the initial information, this was detected on February 7, 2021, at 4:24: AM. A red flag is the time the event took place. The alert also indicates this message was allowed to pass. 

<img width="1842" height="524" alt="image" src="https://github.com/user-attachments/assets/b04c31d0-1a0a-401f-a734-2f45c1df4da5" />

I will create a case and follow the playbook in our SIEM. 

<img width="600" height="414" alt="image" src="https://github.com/user-attachments/assets/34e625ca-f5da-4c90-a6a0-76ed99ca0c20" />


Let's first answer the questions below from the playbook. 
<img width="712" height="408" alt="image" src="https://github.com/user-attachments/assets/10b8d26c-4270-46ea-8d51-57da4e13b07e" />

1) When was it sent? Feb 07, 2021, 04:24 AM
2) What is the email's SMTP address? 172.16.20.3
3) What is the sender's address? john@letsdefend.io
4) What is the recipient address? susie@letsdefend.io
5) Is the mail content suspicious? 
6) Are there any attachments? No

For question 5, I went to the Email Security section of our SIEM to look for the email that was sent. I can see that the message was "Hi Susie, Can we arrange a meeting today if you are available?"
No Attachments. 
<img width="1302" height="398" alt="image" src="https://github.com/user-attachments/assets/66a9110c-b5f2-4367-8220-5ad6c162600b" />


I then wennt ot the Endpoint Security and searched for the Email SMTP Address 172.16.20.3
I found that this had the hostname of the Exchange Server, which handles the organization's emails.


<img width="1862" height="668" alt="image" src="https://github.com/user-attachments/assets/ecc10a3e-257d-49c4-98cf-20f5f5dac031" />



I then went to the log management in our SIEM to look for the Raw Log. I filtered for the date  Feb 07, 2021, to look for any other information that might have been missed in the initial email. I believe it is a false positive. 

<img width="1874" height="708" alt="image" src="https://github.com/user-attachments/assets/c99b91da-c7b0-4a34-a582-2273fe2fbe00" />



I will answer no, there were no attachments or a URL  in the email. 

<img width="700" height="398" alt="image" src="https://github.com/user-attachments/assets/8ed66827-b2a2-42dd-a6c5-2724179db5fd" />


--


## Artifacts 

For the artifacts that we have found to prove that this is a false positive: 
172.16.20.3 - Email Exchange SMTP - IP Address
John@letdefend.io - Senders Address - Email Sender
LetsDefend.io - Domain - E-mail Domain


<img width="684" height="470" alt="image" src="https://github.com/user-attachments/assets/d1aef74d-5fdb-452f-96e7-f534d5aac87d" />


-- 

## Analyst Notes

An alert was generated in the seam on February 7/20/21 at 4:24 AM. The alert involved an internal e-mail sent from John@letdefend.io to susie@letsdefen.io. The email requested a meeting and did not contain any attachments for analysis. The sender and recipient belong to the Letsdefend.io domain. 


<img width="696" height="504" alt="image" src="https://github.com/user-attachments/assets/d395b6a8-0c22-41f6-a77d-8538a5a24006" />


I can now close the case. 

<img width="1698" height="400" alt="image" src="https://github.com/user-attachments/assets/da34cc30-f5f4-42af-b575-623053cccf68" />

I will include the same notes that I've added previously to the close alerts tab and select false positive.


<img width="560" height="624" alt="image" src="https://github.com/user-attachments/assets/598307a7-c662-4904-bf71-175a9bea2293" />


We have now closed the alert. 


<img width="1684" height="438" alt="image" src="https://github.com/user-attachments/assets/9cbc2b40-42fb-4f76-9e52-e9994a837aca" />

This alert was valuable for hands-on experience that highlighted how attacks can originate internally and how some alerts may be false positives. Understanding how to properly investigate and manage these scenarios is important for maintaining SOC efficiency. 



## Recommended Remediation Steps

Going forward, refining email security rules will help reduce false positives by clearly identifying trusted internal emails.
-Alert tuning
