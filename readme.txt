================================================================================
                    UNIVERSITY DATABASE USING MYSQL
================================================================================

Welcome to the University Database project! This repository contains a
structured, fully normalized relational database design for managing
university data, built using MySQL.

--------------------------------------------------------------------------------
TABLE OF CONTENTS
--------------------------------------------------------------------------------
1. Database Structure & Entity Relationships
2. Schema Setup
3. Data Insertion
4. Verification

--------------------------------------------------------------------------------
ABOUT THE PROJECT
--------------------------------------------------------------------------------
This project models a typical university environment and includes 11 essential
tables to manage various aspects such as:

* Academics: course, department, prereq, section
* People: student, instructor, advisor
* Facilities & Scheduling: classroom, time_slot
* Relationships: teaches, takes

The repository is structured to take you sequentially from creating the schema
to populating the database and verifying the integrity of the data.

--------------------------------------------------------------------------------
USAGE
--------------------------------------------------------------------------------
1. Review the Structure: Read through structure.md to understand the database
   schema, primary keys, and foreign key relationships.
2. Setup the Database: Run the queries in 01_Schema_Setup.md to initialize the
   database and tables.
3. Insert Sample Data: Execute the INSERT statements provided in
   02_Data_Insertion.md.
4. Verify Your Setup: Use the SQL queries in 03_Verification.md to ensure your
   database was built and populated correctly.

--------------------------------------------------------------------------------
AUTHOR
--------------------------------------------------------------------------------
AtiaAbk
