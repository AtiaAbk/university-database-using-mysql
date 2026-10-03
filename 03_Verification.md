# ✅ University Database \- Verification

Commands used to verify the schema structure, constraints, and data integrity.

## 🔍 Verify Table Relationships

SELECT TABLE\_NAME, COLUMN\_NAME, REFERENCED\_TABLE\_NAME, REFERENCED\_COLUMN\_NAME 

FROM INFORMATION\_SCHEMA.KEY\_COLUMN\_USAGE 

WHERE REFERENCED\_TABLE\_SCHEMA \= 'uni\_db' AND REFERENCED\_TABLE\_NAME IS NOT NULL;

## 📊 Verify Total Row Counts

SELECT 'department' AS Table\_Name, COUNT(\*) AS Total\_Rows FROM department

UNION ALL SELECT 'classroom', COUNT(\*) FROM classroom

UNION ALL SELECT 'time\_slot', COUNT(\*) FROM time\_slot

UNION ALL SELECT 'course', COUNT(\*) FROM course

UNION ALL SELECT 'instructor', COUNT(\*) FROM instructor

UNION ALL SELECT 'student', COUNT(\*) FROM student

UNION ALL SELECT 'prereq', COUNT(\*) FROM prereq

UNION ALL SELECT 'section', COUNT(\*) FROM section

UNION ALL SELECT 'teaches', COUNT(\*) FROM teaches

UNION ALL SELECT 'takes', COUNT(\*) FROM takes

UNION ALL SELECT 'advisor', COUNT(\*) FROM advisor;

## 👁️‍🗨️ Verify Data Insertion

SELECT \* FROM department;

SELECT \* FROM course;

SELECT \* FROM student;