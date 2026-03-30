# 🏥 Hospital Database Creation & Data Migration

## 📊 Project Summary

Designed and implemented a normalized hospital database system by migrating unstructured Excel data into MySQL, improving data integrity, reducing redundancy, and enabling efficient reporting and analysis.


## 📌 Project Overview

This project focuses on designing and implementing a structured relational database system for a hospital that was previously managing its data using Excel files.

As hospital operations scaled, the Excel-based system became inefficient, inconsistent, and prone to errors. The objective of this project was to:

Design a normalized relational database

Migrate existing Excel data into MySQL

Enforce data integrity and business rules

Implement role-based access control

Enable department-level revenue reporting

## 🚨 Problems Identified in the Existing System
### 1. No Unique Identifiers

There were no guaranteed unique IDs for patients, doctors, departments, or appointments.

### 2. Disconnected Relationships

Appointments existed without enforceable links to valid patients or doctors.

### 3. Invalid and Ambiguous Data

Examples:

Gender values like "X"

Appointment statuses like "On Hold"

Inconsistent date formats

### 4. Double Bookings & Past Appointments

Doctors were occasionally double-booked, and some appointments were scheduled in the past.

### 5. Unrestricted Access to Patient Data

All doctors could see all patient records, regardless of role or department.

### 6. No Department-Level Revenue Reporting

There was no structured way to generate monthly revenue summaries.

## 🛠 Solutions Implemented
### ✔ 1. Structured Relational Schema

Designed normalized tables:

Departments

Doctors

Patients

Appointments

Prescriptions

Bills

LabReports

Implemented:

Primary Keys (Auto Increment)

Foreign Key Constraints

Check Constraints

Default timestamps

This ensured referential integrity and eliminated data redundancy.

### ✔ 2. Data Validation & Standardization

Enforced valid gender values (M, F, O)

Restricted appointment status to (Scheduled, Completed, Cancelled)

Converted inconsistent date formats using STR_TO_DATE

Cleaned and migrated Excel-based hospital data into structured tables

### ✔ 3. Trigger for Appointment Validation

Created a BEFORE INSERT trigger on the Appointments table to:

Prevent scheduling appointments in the past

Prevent double booking of doctors at the same time

This ensures operational reliability at the database level.

### ✔ 4. Role-Based Access Control (RBAC)

Implemented a stored procedure that:

Authenticates doctors using credentials

Allows senior doctors to view all patients within their department

Restricts junior doctors to viewing only their assigned patients

This simulates controlled access to sensitive patient data.

### ✔ 5. Monthly Revenue Reporting

Developed a stored procedure to:

Join Bills, Appointments, Doctors, and Departments

Aggregate billing data

Generate department-wise monthly revenue reports

This converts transactional hospital data into actionable business insights.

## 🧰 Technologies Used

MySQL

SQL (DDL, DML)

Triggers

Stored Procedures

Data Migration & Cleaning

Multi-table Joins and Aggregations

## 📚 Key Learnings

Designing normalized relational schemas

Enforcing business rules at the database level

Migrating messy Excel data into structured systems

Implementing role-based data access

Writing analytical stored procedures



