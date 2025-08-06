---

## 📄 opportunities.md 

md
# 📁 Opportunity Object - SOQL Use Cases

Powerful queries to understand your sales pipeline, forecast revenue, and manage deal progress.

---

## 1️⃣ All Open Opportunities

soql
SELECT Id, Name, StageName, Amount, CloseDate 
FROM Opportunity 
WHERE IsClosed = FALSE

✅ Track deals still in progress.


---

2️⃣ Opportunities Closing This Month

SELECT Id, Name, CloseDate, Amount 
FROM Opportunity 
WHERE CloseDate = THIS_MONTH

✅ Short-term revenue outlook.


---

3️⃣ Top 5 Opportunities by Amount

SELECT Id, Name, Amount 
FROM Opportunity 
ORDER BY Amount DESC 
LIMIT 5

✅ Biggest deals in the pipeline.


---

4️⃣ Opportunities Won in the Last 90 Days

SELECT Id, Name, CloseDate 
FROM Opportunity 
WHERE StageName = 'Closed Won' 
AND CloseDate = LAST_N_DAYS:90

✅ Measure recent wins.


---

5️⃣ Opportunities by Sales Rep

SELECT Owner.Name, COUNT(Id) 
FROM Opportunity 
GROUP BY Owner.Name

✅ Sales performance by user.


---

6️⃣ Lost Opportunities with Reason

SELECT Name, StageName, LossReason__c 
FROM Opportunity 
WHERE StageName = 'Closed Lost'

✅ Learn from past failures.


---

7️⃣ Opportunities by Lead Source

SELECT LeadSource, COUNT(Id) 
FROM Opportunity 
GROUP BY LeadSource

✅ Understand where your deals come from.


---

8️⃣ Opportunities Missing Close Dates

SELECT Id, Name 
FROM Opportunity 
WHERE CloseDate = NULL

✅ Data cleanup for incomplete deals.


---

9️⃣ Opportunities Without Contact Role

SELECT Id, Name 
FROM Opportunity 
WHERE Id NOT IN (SELECT OpportunityId FROM OpportunityContactRole)

✅ Ensure people are tied to deals.


---

🔟 Opportunities with Products

SELECT Id, Name, (SELECT Quantity, UnitPrice FROM OpportunityLineItems) 
FROM Opportunity 
WHERE IsClosed = FALSE

✅ View items sold within opportunities.


---