# ✅ University Database - Verification

Commands used to verify the schema structure, constraints, and data integrity.

---

## 🔍 Verify Table Relationships

```sql
SELECT TABLE_NAME, COLUMN_NAME, REFERENCED_TABLE_NAME, REFERENCED_COLUMN_NAME
FROM INFORMATION_SCHEMA.KEY_COLUMN_USAGE
WHERE REFERENCED_TABLE_SCHEMA = 'uni_db' AND REFERENCED_TABLE_NAME IS NOT NULL;
```

---

## 📊 Verify Total Row Counts

```sql
SELECT 'department' AS Table_Name, COUNT(*) AS Total_Rows FROM department
UNION ALL SELECT 'classroom', COUNT(*) FROM classroom
UNION ALL SELECT 'time_slot', COUNT(*) FROM time_slot
UNION ALL SELECT 'course', COUNT(*) FROM course
UNION ALL SELECT 'instructor', COUNT(*) FROM instructor
UNION ALL SELECT 'student', COUNT(*) FROM student
UNION ALL SELECT 'prereq', COUNT(*) FROM prereq
UNION ALL SELECT 'section', COUNT(*) FROM section
UNION ALL SELECT 'teaches', COUNT(*) FROM teaches
UNION ALL SELECT 'takes', COUNT(*) FROM takes
UNION ALL SELECT 'advisor', COUNT(*) FROM advisor;
```

---

## 👁️‍🗨️ Verify Data Insertion

```sql
SELECT * FROM department;
SELECT * FROM course;
SELECT * FROM student;
```

---

> **Author:** [AtiaAbk](https://github.com/AtiaAbk)
