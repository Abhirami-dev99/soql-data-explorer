---

## 📄 cases.md 

md
# 📁 Case Object - SOQL Use Cases

Key queries to track support workload, case resolution, and customer satisfaction.

---

## 1️⃣ All Open Cases

soql
SELECT Id, CaseNumber, Subject, Status 
FROM Case 
WHERE IsClosed = FALSE

✅ Identify tickets still being worked on.


---

2️⃣ Cases Closed in the Last 7 Days

SELECT Id, Subject, ClosedDate 
FROM Case 
WHERE ClosedDate = LAST_N_DAYS:7

✅ Track recent support activity.


---

3️⃣ Cases by Priority

SELECT Priority, COUNT(Id) 
FROM Case 
GROUP BY Priority

✅ Understand workload severity.


---

4️⃣ High Priority Open Cases

SELECT Id, CaseNumber, Subject, Priority 
FROM Case 
WHERE Priority = 'High' AND IsClosed = FALSE

✅ Focus on urgent issues.


---

5️⃣ Cases Assigned to a Specific User

SELECT Id, CaseNumber, Subject, Owner.Name 
FROM Case 
WHERE Owner.Username = 'support.agent@example.com'

✅ Monitor team workload.


---

6️⃣ Average Resolution Time by Type

SELECT Type, AVG(Days_Open__c) 
FROM Case 
WHERE IsClosed = TRUE 
GROUP BY Type

✅ Custom field needed to track days open.


---

7️⃣ Cases Without Contact Info

SELECT Id, CaseNumber, ContactId 
FROM Case 
WHERE ContactId = NULL

✅ Data quality check for orphaned cases.


---

8️⃣ Cases Created This Month by Channel

SELECT Origin, COUNT(Id) 
FROM Case 
WHERE CreatedDate = THIS_MONTH 
GROUP BY Origin

✅ Volume by support channel (Web, Phone, Email, etc).


---

9️⃣ Escalated Cases

SELECT Id, CaseNumber, Subject 
FROM Case 
WHERE IsEscalated = TRUE

✅ Follow up on escalated customer issues.


---

🔟 Case Count by Status

SELECT Status, COUNT(Id) 
FROM Case 
GROUP BY Status

✅ Quick dashboard-style report.


---