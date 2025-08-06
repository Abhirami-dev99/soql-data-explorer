---

## 📄 contacts.md 

# 📁 Contact Object - SOQL Use Cases

Real-world SOQL queries to fetch and analyze contact data in Salesforce. These help understand relationships and manage communications effectively.

---

## 1️⃣ All Contacts with Email and Phone

```soql
SELECT Id, FirstName, LastName, Email, Phone 
FROM Contact 
WHERE Email != NULL AND Phone != NULL

✅ Useful for communication campaigns.


---

2️⃣ Recently Created Contacts

SELECT Id, FirstName, LastName, CreatedDate 
FROM Contact 
WHERE CreatedDate = LAST_N_DAYS:30

✅ Monitor new leads or entries.


---

3️⃣ Contacts Without Accounts (Orphan Contacts)

SELECT Id, FirstName, LastName 
FROM Contact 
WHERE AccountId = NULL

✅ Identifies unlinked or standalone contacts.


---

4️⃣ Contacts Related to a Specific Account

SELECT Id, FirstName, LastName, Account.Name 
FROM Contact 
WHERE Account.Name = 'Acme Corporation'

✅ View people associated with a particular company.


---

5️⃣ Contacts by Mailing State

SELECT Id, FirstName, LastName, MailingState 
FROM Contact 
WHERE MailingState = 'California'

✅ Target contacts in specific geographic regions.


---

6️⃣ Contacts with No Opportunities via Account

SELECT Id, FirstName, LastName 
FROM Contact 
WHERE AccountId NOT IN (SELECT AccountId FROM Opportunity)

✅ Find people in cold or neglected accounts.


---

7️⃣ Contacts Modified Recently

SELECT Id, FirstName, LastName, LastModifiedDate 
FROM Contact 
WHERE LastModifiedDate = LAST_N_DAYS:15

✅ Track recent updates.


---

8️⃣ Contacts with Birthdays This Month

SELECT Id, FirstName, LastName, Birthdate 
FROM Contact 
WHERE CALENDAR_MONTH(Birthdate) = THIS_MONTH

✅ Great for birthday greetings and campaigns.


---

9️⃣ Contacts with Open Activities

SELECT Id, FirstName, LastName, (SELECT Subject FROM Activities WHERE IsClosed = FALSE) 
FROM Contact

✅ See pending tasks or events related to each contact.


---

🔟 Number of Contacts per Title

SELECT Title, COUNT(Id) 
FROM Contact 
GROUP BY Title

✅ Analyze role distribution in your contact base.


---