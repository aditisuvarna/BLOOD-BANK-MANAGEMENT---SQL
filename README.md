# 🩸 BLOOD-BANK-MANAGEMENT---SQL
This project manages donor details, hospital information, and blood inventories. It helps track blood donations, organize 🏕️ donation drives, and maintain 📦 stock levels. SQL queries are used to fetch key insights like  🌟 top donors, 📍 active locations, and 🏥 hospital lists. Designed for efficient blood bank operations and strategic planning.

# 📘 Introduction
🩸Blood is a vital resource that saves millions of lives every year, yet managing its availability, safety, and distribution is a major challenge for healthcare institutions.

 The Blood Bank Management System is designed to streamline and enhance the processes involved in 🙋‍♂️ donor management, 🏪 blood inventory tracking, 🏥 hospital/clinic coordination,🧑‍⚕️ patient requests, 👨‍🔬 staff management, and 🧪 blood testing.

 This project uses SQL to build a comprehensive database that supports real-time management of 🩸blood donations, 🧊 storage, 🧪 testing, and 🚑 distribution, ensuring that critical blood supplies are effectively maintained and safely delivered when needed.
 
# 🎯 Objective
To design a relational database that stores and manages information related to blood donors, donations, inventory, hospitals, clinics, and patients.

To automate and optimize the process of tracking blood donations, tests, and supply to minimize wastage and enhance availability.

To facilitate efficient matching of blood groups between donors and patients during emergencies.

To enable easy retrieval of insights through SQL queries for operational and strategic decision-making.

# ❗Problem Statement
Blood banks often face challenges such as inventory shortages, expired blood units, donor eligibility management, and 📞 inefficient communication with hospitals. Manual systems or fragmented databases can result in delays, errors, and loss of precious resources. Hence, there is a need for a centralized and systematic database solution that manages end-to-end operations including donor registration, blood collection, testing for safety, tracking available inventory, responding to hospital requests, and issuing blood units to patients.

# 📊 Data Overview
- 👤 Donors: Donor details and eligibility tracking.

- 🙋 Patients: Patient details and blood request requirements.

- 🩸 Blood_Inventory: Blood unit stock management.

- 📝 Blood_Requests: Blood requests raised by hospitals.

- 🏥 Hospitals_or_Clinics: Hospitals connected to the blood bank.

- 👨‍⚕️ Staff: Staff information managing donations and transactions.

- 🧾 Donation_Record: Record of each blood donation.
  
- 🧪 Blood_Tests: Blood testing results (HIV, Malaria, Hepatitis).

- 💳 Transactions: Blood issuance to patients.

- 🏕️ Donation_Camp: Organization of blood donation camps.

# 🧬 ER DIAGRAM
"Our database design mainly follows one-to-many relationships ➕.
Examples include:

- One donor ➡️ many donations
  
- One hospital ➡️ many requests
  
- One staff member ➡️ many activities"

# 🔍 Queries & Analysis

### 1️⃣ Find the total number of patients registered
```sql
 SELECT COUNT(*) AS total_patients  
 FROM Patients;
```

### 2️⃣ Get all eligible donors
```sql
SELECT * FROM Donors WHERE is_eligible = TRUE;
```

### 3️⃣ Total quantity of each blood group in inventory
```sql
SELECT blood_group, SUM(quantity_ml) AS total_quantity
FROM Blood_Inventory
WHERE status = 'Available'
GROUP BY blood_group;
```
### 4️⃣ Find the total expired blood units for each blood group
```sql
SELECT blood_group, COUNT(*) AS expired_count
FROM Blood_Inventory
WHERE expiry_date < CURDATE()
GROUP BY blood_group;
```

### 5️⃣ List patients issued more than 2 units of blood
```sql
SELECT p.name, SUM(t.units_issued) AS total_units
FROM Patients p
JOIN Transactions t ON p.patient_id = t.patient_id
GROUP BY p.patient_id
HAVING total_units > 2;
```

### 6️⃣ Top 5 hospitals with the highest number of blood requests
```sql
SELECT name, total_requests
FROM Hospitals_Or_Clinics
ORDER BY total_requests DESC
LIMIT 5;
```

### 7️⃣ Blood group issued the most — and total number of units issued per blood group
```sql
SELECT t.blood_group, COUNT(*) AS total_issued
FROM Transactions t
GROUP BY t.blood_group
ORDER BY total_issued DESC;
```

### 8️⃣ Identify the staff member who has handled the highest number of blood donations
```sql
SELECT s.name, COUNT(dr.donation_id) AS total_handled
FROM Staff s
JOIN Donation_Records dr ON s.staff_id = dr.staff_id
GROUP BY s.staff_id
ORDER BY total_handled DESC
LIMIT 1;
```

### 9️⃣ Top 3 donors with highest total quantity of blood donated
```sql
SELECT d.name, SUM(dr.quantity_ml) AS total_donated
FROM Donors d
JOIN Donation_Records dr ON d.donor_id = dr.donor_id
GROUP BY d.donor_id
ORDER BY total_donated DESC
LIMIT 3;
```

### 🔟 Identify understocked blood types (<1000ml)
```sql
SELECT blood_group, SUM(quantity_ml) AS total_stock
FROM Blood_Inventory
GROUP BY blood_group
HAVING total_stock < 1000;
```

### 1️⃣1️⃣ Which donors contributed the most blood
```sql
SELECT d.name, SUM(dr.quantity_ml) AS total_donated
FROM Donors d
JOIN Donation_Records dr ON d.donor_id = dr.donor_id
GROUP BY d.donor_id;
```

### 1️⃣2️⃣ Find the blood group with the highest stock in the inventory
```sql
SELECT blood_group, SUM(quantity_ml) AS total_quantity
FROM Blood_Inventory
GROUP BY blood_group
ORDER BY total_quantity DESC
LIMIT 1;
```

### 1️⃣3️⃣ List all hospitals in a particular city
```sql
SELECT name FROM hospitals_or_clinics WHERE city = 'Mumbai';
```

### 1️⃣4️⃣ Total blood donations made by blood group
```sql
SELECT blood_group, COUNT(*) AS donation_count
FROM Donation_Records
GROUP BY blood_group;
```
### 1️⃣5️⃣ Find how many blood donation camps were organized at each location
```sql
SELECT location, COUNT(*) AS number_of_camps
FROM Donation_Camp
GROUP BY location
ORDER BY number_of_camps DESC;
```
# Conclusion
- Identified understocked blood groups to avoid shortages.
- Found top hospitals and donors for better planning.
- Highlighted need for expiry management to reduce wastage.
- Improved visibility into staff performance and operations.
- Help blood banks maintain efficient and reliable inventory.



















