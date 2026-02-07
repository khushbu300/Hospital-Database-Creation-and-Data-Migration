# Hospital-Database-Creation-and-Data-Migration

Hospital Database Creation & Data Migration (MySQL)

This project focuses on designing a relational hospital database and migrating data from a single Excel file into a structured MySQL database.
The goal is to convert a large, denormalized dataset into normalized tables while enforcing business rules, data validation, and basic role-based access logic.

The project is based on a real-world styled dataset containing hospital operational data such as doctors, patients, appointments, prescriptions, lab reports and billing information.

Project Overview

Hospitals often maintain operational data in spreadsheets, which becomes difficult to manage as data grows.
In this project, a single Excel/CSV file is used as the source and migrated into a properly designed relational database.

The implementation covers:

Database schema design

Data migration from Excel to MySQL

Data integrity and validation rules

Business rule automation using triggers

Reporting using stored procedures

Source Data

The source file contains data for multiple entities in a single sheet.
Columns are prefixed to represent different entities, such as:

Departments

Doctors

Patients

Appointments

Prescriptions

Lab reports

Bills

This staging table is used to populate the final normalized tables.

Tools and Technologies

MySQL 8.x

MySQL Workbench

Excel / CSV (source file)

Database Structure

The database is normalized into the following tables:

departments

doctors

patients

appointments

prescriptions

labreports

bills

doctor_credentials

Foreign key relationships are implemented to maintain referential integrity between departments, doctors, patients and appointments.

Main Features
Data integrity and validation

Unique identifiers are created using auto-increment primary keys.

Gender values are restricted to M, F and O.

Appointment status is restricted to Scheduled, Completed and Cancelled.

Appointment scheduling rules

Triggers are used to prevent:

appointments being scheduled in the past

a doctor being booked for more than one appointment at the same time

These checks are performed automatically during insertion (and update) of appointment records.

Role-based patient data access

A stored procedure is created to allow doctors to view patient data based on their role.

Senior doctors can view patients within their department.

Other doctors can view only their own patients and related medical information.

This simulates controlled access to sensitive patient data at the database level.

Monthly revenue reporting

A stored procedure is implemented to generate department-wise monthly revenue using billing data.
The procedure accepts year and month as input parameters and returns total revenue per department.

Data Migration

Data is first loaded into a staging table created from the original Excel/CSV file.
From this staging table, data is inserted into normalized tables using INSERT … SELECT statements.

During migration:

date and datetime values are converted into proper formats

empty and invalid rows are filtered

relationships between entities are preserved

How to Run

Create the database and tables using the provided SQL script.

Import the Excel/CSV file as a staging table (for example, hospital_data).

Execute the data migration queries.

Create triggers and stored procedures.

Test using sample procedure calls and insert statements.

Example:

CALL VIEW_DOCTOR_DATA('doctor1','password');
CALL SP_MONTHLYREVENUE(2025,5);

What this project demonstrates

Designing a relational database from a real, denormalized dataset

Implementing foreign key relationships and constraints

Cleaning and transforming data during migration

Enforcing business rules using triggers

Using stored procedures for reporting and controlled data access

Author

Khushbu Shahare
