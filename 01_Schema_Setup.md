# 🏢 University Database \- Schema Setup

This section contains the structural setup of the University Database. All 11 tables are created here with their appropriate data types and constraints.

## 🛠️ Create Database

CREATE DATABASE uni\_db;

USE uni\_db;

## 🏗️ Create Tables

CREATE TABLE department (

    dept\_name VARCHAR(20) NOT NULL,

    building VARCHAR(15) NOT NULL,

    budget DECIMAL(12,2) NOT NULL,

    PRIMARY KEY (dept\_name)

);

CREATE TABLE classroom (

    building VARCHAR(15) NOT NULL,

    room\_no VARCHAR(7) NOT NULL,

    capacity SMALLINT NOT NULL,

    PRIMARY KEY (building, room\_no)

);

CREATE TABLE time\_slot (

    time\_slot\_id VARCHAR(4) NOT NULL,

    day VARCHAR(1) NOT NULL,

    start\_time TIME NOT NULL,

    end\_time TIME NOT NULL,

    PRIMARY KEY (time\_slot\_id, day, start\_time)

);

CREATE TABLE course (

    course\_id VARCHAR(8) NOT NULL,

    title VARCHAR(50) NOT NULL,

    dept\_name VARCHAR(20),

    credits TINYINT NOT NULL,

    PRIMARY KEY (course\_id),

    FOREIGN KEY (dept\_name) REFERENCES department(dept\_name)

);

CREATE TABLE instructor (

    ID INT NOT NULL,

    name VARCHAR(20) NOT NULL,

    dept\_name VARCHAR(20),

    salary DECIMAL(8,2) NOT NULL,

    PRIMARY KEY (ID),

    FOREIGN KEY (dept\_name) REFERENCES department(dept\_name)

);

CREATE TABLE student (

    ID INT NOT NULL,

    name VARCHAR(20) NOT NULL,

    dept\_name VARCHAR(20),

    tot\_cred SMALLINT NOT NULL,

    PRIMARY KEY (ID),

    FOREIGN KEY (dept\_name) REFERENCES department(dept\_name)

);

CREATE TABLE prereq (

    course\_id VARCHAR(8) NOT NULL,

    prereq\_id VARCHAR(8) NOT NULL,

    PRIMARY KEY (course\_id, prereq\_id),

    FOREIGN KEY (course\_id) REFERENCES course(course\_id),

    FOREIGN KEY (prereq\_id) REFERENCES course(course\_id)

);

CREATE TABLE section (

    course\_id VARCHAR(8) NOT NULL,

    sec\_id VARCHAR(8) NOT NULL,

    semester VARCHAR(6) NOT NULL,

    year SMALLINT NOT NULL,

    building VARCHAR(15),

    room\_no VARCHAR(7),

    time\_slot\_id VARCHAR(4),

    PRIMARY KEY (course\_id, sec\_id, semester, year),

    FOREIGN KEY (course\_id) REFERENCES course(course\_id),

    FOREIGN KEY (building, room\_no) REFERENCES classroom(building, room\_no)

);

CREATE TABLE teaches (

    ID INT NOT NULL,

    course\_id VARCHAR(8) NOT NULL,

    sec\_id VARCHAR(8) NOT NULL,

    semester VARCHAR(6) NOT NULL,

    year SMALLINT NOT NULL,

    PRIMARY KEY (ID, course\_id, sec\_id, semester, year),

    FOREIGN KEY (ID) REFERENCES instructor(ID),

    FOREIGN KEY (course\_id, sec\_id, semester, year) REFERENCES section(course\_id, sec\_id, semester, year)

);

CREATE TABLE takes (

    ID INT NOT NULL,

    course\_id VARCHAR(8) NOT NULL,

    sec\_id VARCHAR(8) NOT NULL,

    semester VARCHAR(6) NOT NULL,

    year SMALLINT NOT NULL,

    grade VARCHAR(2),

    PRIMARY KEY (ID, course\_id, sec\_id, semester, year),

    FOREIGN KEY (ID) REFERENCES student(ID),

    FOREIGN KEY (course\_id, sec\_id, semester, year) REFERENCES section(course\_id, sec\_id, semester, year)

);

CREATE TABLE advisor (

    s\_id INT NOT NULL,

    i\_id INT,

    PRIMARY KEY (s\_id),

    FOREIGN KEY (s\_id) REFERENCES student(ID),

    FOREIGN KEY (i\_id) REFERENCES instructor(ID)

);