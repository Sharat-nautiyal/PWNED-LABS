**Unlock Access with Azure Key Vault**

This was a great real world CTF, to test how secure are the secrets saved in Azure Key Vault service and also understand risk of misconfigured 3rd party supply chain attacks. Least privilege access, real time Cloud Detection and Response are critical security controls.

The CTF gives a brief overview of the task that we need to complete as red team/offensive team/penetration testers. 

**🎯 Scenario**
After successfully compromising the Azure user account marcus@megabigtech.com and gaining access to their cloud environment, Mega Big Tech have asked us to see how far we can penetrate into the cloud environment, and if we can access any confidential data. Specifically they need us to assess the security of resources associated with the Azure Subscription ID ceff06cb-e29d-4486-a3ae-eaaec5689f94 .

We’ve been provided with the credentials for Marcus, an employee at Mega Big Tech. With these, we log into the Azure portal to begin our mission. 🔑💼



![image](https://github.com/user-attachments/assets/8c145a20-c196-438b-b36f-f163ce467a97)


**🔍 Enumeration of Azure Key Vault Service 🔑**
Once inside, we start by enumerating the account and discover that Marcus has access to the Azure Key Vault. 💼🔐

![image](https://github.com/user-attachments/assets/90bde5dd-574b-41ce-9012-7ab1764e18d1)


Inside the ext-contractor key vault, we find three contractor names. These individuals likely work for Mega Big Tech. 🤔👥

![image](https://github.com/user-attachments/assets/262d0086-21e6-4710-b0b4-a52d7bc71f3d)


We then proceed to click on each key to reveal their secrets. Below is a snapshot of one user’s secrets, but you’ll need to repeat this process for all three to gather the full intel. 📜🔎

When we enumerate Josh-harvey, we find their secrets/password.


![image](https://github.com/user-attachments/assets/ddf184b3-0872-44bc-b079-201aecbd94d4)


**Lateral Movement to Another Azure Tenant 🔄🏢**
Sweet! We've uncovered secrets for Josh-Harvey and others. 😏 But we hit a snag—while we have their credentials, we don’t know their usernames since these contractors work for another company. 🕵️♀️

No worries, though! We head over to EntraID to search for these users. In the snapshot below, we’re searching for Josh. You’ll want to repeat this for all three contractors. 🔎📂

![image](https://github.com/user-attachments/assets/fee4992f-f6a9-4b9a-83bb-a38965f4e02a)


Now that we know what are the contracts login email address and we already have secrets from the last steps. We go to portal.azure[.]com and try the credentials.

**Enumeration of Azure Storage Accounts 📦📂**
Interesting… Josh has access to various services. I’m particularly intrigued by the Azure Storage Accounts service, so let’s dive into that next. 💼📥

![image](https://github.com/user-attachments/assets/5b838715-9456-458b-8453-b40f66417f28)



Interesting, I can see Josh has access to many types of services. I am interested to see the Azure Storage Accounts service, so I click on it to enumerate it.

**Enumeration of Azure Storage Accounts 🌐💣**
Looks like there are some Tables in the storage accounts. These are the noSQL tables, so let's explore it to see if we can find anything interesting.

![image](https://github.com/user-attachments/assets/bbbf9f9a-e565-4b27-ac55-8361e8511b52)


It turns out there are some NoSQL Tables in these storage accounts. Let’s explore them to see if we can dig up anything juicy. 🔍💻

And what do we find? Woah! The customers table is exposing sensitive data like credit card numbers, customer names, IDs, and CVVs. 😱💳

Oh, and let’s not forget—the flag is right there at the bottom to complete our CTF challenge. 🏁🎉

![image](https://github.com/user-attachments/assets/719f4527-6984-4f57-b38a-6d220068ffc6)

