---

📄 accounts.md 

# 📁 Account Object - SOQL Use Cases

A collection of commonly used and practical SOQL queries on the Account object in Salesforce. These queries help admins, developers, and analysts retrieve insightful data.

---

## 1️⃣ Get All Active Accounts

```soql
SELECT Id, Name, Industry, Rating 
FROM Account 
WHERE IsActive__c = TRUE

✅ Shows all currently active customers.


---

2️⃣ Accounts Without Opportunities

SELECT Id, Name 
FROM Account 
WHERE Id NOT IN (SELECT AccountId FROM Opportunity)

✅ Helps identify neglected accounts without any sales activity.


---

3️⃣ Top 5 Accounts by Annual Revenue

SELECT Id, Name, AnnualRevenue 
FROM Account 
ORDER BY AnnualRevenue DESC 
LIMIT 5

✅ Useful for targeting your most valuable clients.


---

4️⃣ Recently Created Accounts (Last 30 Days)

SELECT Id, Name, CreatedDate 
FROM Account 
WHERE CreatedDate = LAST_N_DAYS:30

✅ Tracks new accounts added recently.


---

5️⃣ Accounts Owned by a Specific User

SELECT Id, Name, Owner.Name 
FROM Account 
WHERE Owner.Username = 'john.doe@example.com'

✅ Retrieves accounts managed by a specific user.


---

6️⃣ Accounts with Open Opportunities

SELECT Id, Name 
FROM Account 
WHERE Id IN (SELECT AccountId FROM Opportunity WHERE IsClosed = FALSE)

✅ Focuses on accounts currently in the sales pipeline.


---

7️⃣ Accounts by Type and Industry

SELECT Name, Type, Industry 
FROM Account 
WHERE Type = 'Customer' AND Industry = 'Technology'

✅ Segment customers within a specific industry.


---

8️⃣ Accounts with Related Contacts

SELECT Id, Name, (SELECT Id, FirstName, LastName, Email FROM Contacts) 
FROM Account 
WHERE CreatedDate = LAST_N_DAYS:60

✅ Parent-to-child query showing recent accounts and their contacts.


---

9️⃣ Number of Accounts Grouped by Rating

SELECT Rating, COUNT(Id) 
FROM Account 
GROUP BY Rating

✅ Quick report to understand the distribution of account ratings.


---

🔟 Accounts with Billing State = California

SELECT Id, Name, BillingState 
FROM Account 
WHERE BillingState = 'California'

✅ Geographic filtering by billing address.


---

🧠 Tip: You can extend these queries with WITH SECURITY_ENFORCED to respect sharing rules and field-level security, like this:

SELECT Id, Name FROM Account WITH SECURITY_ENFORCED