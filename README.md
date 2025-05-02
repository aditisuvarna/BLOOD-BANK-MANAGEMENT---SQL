# BLOOD-BANK-MANAGEMENT---SQL
This project manages donor details, hospital information, and blood inventories. It helps track blood donations, organize donation drives, and maintain stock levels. SQL queries are used to fetch key insights like top donors, active locations, and hospital lists. Designed for efficient blood bank operations and strategic planning.

# Introduction
Blood is a vital resource that saves millions of lives every year, yet managing its availability, safety, and distribution is a major challenge for healthcare institutions.

 The Blood Bank Management System is designed to streamline and enhance the processes involved in donor management, blood inventory tracking, hospital/clinic coordination, patient requests, staff management, and blood testing.

 This project uses SQL to build a comprehensive database that supports real-time management of blood donations, storage, testing, and distribution, ensuring that critical blood supplies are effectively maintained and safely delivered when needed.
 
# Objective
To design a relational database that stores and manages information related to blood donors, donations, inventory, hospitals, clinics, and patients.

To automate and optimize the process of tracking blood donations, tests, and supply to minimize wastage and enhance availability.

To facilitate efficient matching of blood groups between donors and patients during emergencies.

To enable easy retrieval of insights through SQL queries for operational and strategic decision-making.

# Problem Statement
Blood banks often face challenges such as inventory shortages, expired blood units, donor eligibility management, and inefficient communication with hospitals. Manual systems or fragmented databases can result in delays, errors, and loss of precious resources. Hence, there is a need for a centralized and systematic database solution that manages end-to-end operations including donor registration, blood collection, testing for safety, tracking available inventory, responding to hospital requests, and issuing blood units to patients.

# Data Overview
Donors: Donor details and eligibility tracking.

Patients: Patient details and blood request requirements.

Blood_Inventory: Blood unit stock management.

Blood_Requests: Blood requests raised by hospitals.

Hospitals_or_Clinics: Hospitals connected to the blood bank.

Staff: Staff information managing donations and transactions.

Donation_Record: Record of each blood donation.

Blood_Tests: Blood testing results (HIV, Malaria, Hepatitis).

Transactions: Blood issuance to patients.

Donation_Camp: Organization of blood donation camps.

# ER DIAGRAM
"Our database design mainly follows one-to-many relationships,  for example, one donor giving multiple donations, one hospital making multiple requests, and one staff managing multiple activities."

# QUERIES & ANALYSIS

# 1. Find the total number of patients registered

## SELECT COUNT(*) AS total_patients  
## FROM Patients;

# Result: total_patients = 25

# 2. Find all eligible donors


# SELECT * FROM Donors WHERE is_eligible = TRUE;
