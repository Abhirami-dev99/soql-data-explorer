---

📄 custom-objects.md (for Customer__c)

# 📁 Custom Object - Customer__c SOQL Use Cases

These sample SOQL queries help interact with a custom object Customer__c. You can adapt them based on your actual field names and business needs.

---

## 1️⃣ Get All Active Customers

```soql
SELECT Id, Name, Status__c, CreatedDate 
FROM Customer__c 
WHERE Status__c = 'Active'

✅ Lists currently active customers.


---

2️⃣ Recently Added Customers

SELECT Id, Name, CreatedDate 
FROM Customer__c 
WHERE CreatedDate = LAST_N_DAYS:30

✅ Monitor new customer acquisition.


---

3️⃣ Customers by Type

SELECT Type__c, COUNT(Id) 
FROM Customer__c 
GROUP BY Type__c

✅ Shows distribution by customer type.


---

4️⃣ Customers Without Assigned Account Manager

SELECT Id, Name 
FROM Customer__c 
WHERE Account_Manager__c = NULL

✅ Find records missing ownership.


---

5️⃣ High-Value Customers

SELECT Id, Name, Annual_Spend__c 
FROM Customer__c 
WHERE Annual_Spend__c > 100000 
ORDER BY Annual_Spend__c DESC

✅ Target top spenders.


---

6️⃣ Customers in a Specific Region

SELECT Id, Name, Region__c 
FROM Customer__c 
WHERE Region__c = 'North America'

✅ Segment by region.


---

7️⃣ Customers with Recent Interactions

SELECT Id, Name, Last_Interaction_Date__c 
FROM Customer__c 
WHERE Last_Interaction_Date__c = LAST_N_DAYS:15

✅ Shows engagement trends.


---

8️⃣ Customers with Related Orders (Child Records)

SELECT Id, Name, (SELECT Id, Name, Status_c FROM Orders_r) 
FROM Customer__c

✅ Parent-to-child query showing customer orders.


---

9️⃣ Customers with Missing Key Info

SELECT Id, Name 
FROM Customer__c 
WHERE Email_c = NULL OR Phone_c = NULL

✅ Data quality check.


---

🔟 Customers Grouped by Satisfaction Level

SELECT Satisfaction_Score__c, COUNT(Id) 
FROM Customer__c 
GROUP BY Satisfaction_Score__c

✅ Understand customer sentiment.


---