# 🏢 University Database - Schema Setup

This section contains the structural setup of the University Database. All 11 tables are created here with their appropriate data types and constraints.

---

## 🛠️ Create Database

```sql
CREATE DATABASE uni_db;
USE uni_db;
```

---

## 🏗️ Create Tables

```sql
CREATE TABLE department (
    dept_name VARCHAR(20) NOT NULL,
    building VARCHAR(15) NOT NULL,
    budget DECIMAL(12,2) NOT NULL,
    PRIMARY KEY (dept_name)
);

CREATE TABLE classroom (
    building VARCHAR(15) NOT NULL,
    room_no VARCHAR(7) NOT NULL,
    capacity SMALLINT NOT NULL,
    PRIMARY KEY (building, room_no)
);

CREATE TABLE time_slot (
    time_slot_id VARCHAR(4) NOT NULL,
    day VARCHAR(1) NOT NULL,
    start_time TIME NOT NULL,
    end_time TIME NOT NULL,
    PRIMARY KEY (time_slot_id, day, start_time)
);

CREATE TABLE course (
    course_id VARCHAR(8) NOT NULL,
    title VARCHAR(50) NOT NULL,
    dept_name VARCHAR(20),
    credits TINYINT NOT NULL,
    PRIMARY KEY (course_id),
    FOREIGN KEY (dept_name) REFERENCES department(dept_name)
);

CREATE TABLE instructor (
    ID INT NOT NULL,
    name VARCHAR(20) NOT NULL,
    dept_name VARCHAR(20),
    salary DECIMAL(8,2) NOT NULL,
    PRIMARY KEY (ID),
    FOREIGN KEY (dept_name) REFERENCES department(dept_name)
);

CREATE TABLE student (
    ID INT NOT NULL,
    name VARCHAR(20) NOT NULL,
    dept_name VARCHAR(20),
    tot_cred SMALLINT NOT NULL,
    PRIMARY KEY (ID),
    FOREIGN KEY (dept_name) REFERENCES department(dept_name)
);

CREATE TABLE prereq (
    course_id VARCHAR(8) NOT NULL,
    prereq_id VARCHAR(8) NOT NULL,
    PRIMARY KEY (course_id, prereq_id),
    FOREIGN KEY (course_id) REFERENCES course(course_id),
    FOREIGN KEY (prereq_id) REFERENCES course(course_id)
);

CREATE TABLE section (
    course_id VARCHAR(8) NOT NULL,
    sec_id VARCHAR(8) NOT NULL,
    semester VARCHAR(6) NOT NULL,
    year SMALLINT NOT NULL,
    building VARCHAR(15),
    room_no VARCHAR(7),
    time_slot_id VARCHAR(4),
    PRIMARY KEY (course_id, sec_id, semester, year),
    FOREIGN KEY (course_id) REFERENCES course(course_id),
    FOREIGN KEY (building, room_no) REFERENCES classroom(building, room_no)
);

CREATE TABLE teaches (
    ID INT NOT NULL,
    course_id VARCHAR(8) NOT NULL,
    sec_id VARCHAR(8) NOT NULL,
    semester VARCHAR(6) NOT NULL,
    year SMALLINT NOT NULL,
    PRIMARY KEY (ID, course_id, sec_id, semester, year),
    FOREIGN KEY (ID) REFERENCES instructor(ID),
    FOREIGN KEY (course_id, sec_id, semester, year) REFERENCES section(course_id, sec_id, semester, year)
);

CREATE TABLE takes (
    ID INT NOT NULL,
    course_id VARCHAR(8) NOT NULL,
    sec_id VARCHAR(8) NOT NULL,
    semester VARCHAR(6) NOT NULL,
    year SMALLINT NOT NULL,
    grade VARCHAR(2),
    PRIMARY KEY (ID, course_id, sec_id, semester, year),
    FOREIGN KEY (ID) REFERENCES student(ID),
    FOREIGN KEY (course_id, sec_id, semester, year) REFERENCES section(course_id, sec_id, semester, year)
);

CREATE TABLE advisor (
    s_id INT NOT NULL,
    i_id INT,
    PRIMARY KEY (s_id),
    FOREIGN KEY (s_id) REFERENCES student(ID),
    FOREIGN KEY (i_id) REFERENCES instructor(ID)
);
```

---

> **Author:** [AtiaAbk](https://github.com/AtiaAbk)
