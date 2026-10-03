# 🗂️ Database Structure & Entity Relationships

This section defines the architecture of the 11 tables used in the database. It highlights the Primary Keys (PK) used for unique identification and the Foreign Keys (FK) used to establish relationships between tables.

---

## 🏗️ Schema Overview

| Table Name | Primary Key (PK) | Foreign Key (FK) -> References |
| :--- | :--- | :--- |
| **department** | `dept_name` | *None* (Base Table) |
| **classroom** | `building`, `room_no` | *None* (Base Table) |
| **time_slot** | `time_slot_id`, `day`, `start_time` | *None* (Base Table) |
| **course** | `course_id` | `dept_name` -> `department(dept_name)` |
| **instructor** | `ID` | `dept_name` -> `department(dept_name)` |
| **student** | `ID` | `dept_name` -> `department(dept_name)` |
| **prereq** | `course_id`, `prereq_id` | `course_id` -> `course(course_id)` <br> `prereq_id` -> `course(course_id)` |
| **section** | `course_id`, `sec_id`, `semester`, `year` | `course_id` -> `course(course_id)` <br> `building`, `room_no` -> `classroom(building, room_no)` |
| **teaches** | `ID`, `course_id`, `sec_id`, `semester`, `year` | `ID` -> `instructor(ID)` <br> `course_id`, `sec_id`, `semester`, `year` -> `section(PK)` |
| **takes** | `ID`, `course_id`, `sec_id`, `semester`, `year` | `ID` -> `student(ID)` <br> `course_id`, `sec_id`, `semester`, `year` -> `section(PK)` |
| **advisor** | `s_id` | `s_id` -> `student(ID)` <br> `i_id` -> `instructor(ID)` |

---

## 🔗 Key Relationship Summary

* The **`department`** table acts as the central hub for mapping `course`, `instructor`, and `student` via the `dept_name` attribute.
* The **`section`** table links physical spaces (`classroom`) with academic offerings (`course`).
* The **`teaches`** and **`takes`** tables act as many-to-many relationship resolvers connecting people (`instructor`/`student`) to specific `section` schedules.

---

> **Author:** [AtiaAbk](https://github.com/AtiaAbk)
