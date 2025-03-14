#  📌 Education Industry Uplink-College-Database

## Design-and-Implementation-Report

**1️⃣ Introduction**

📌 Project Overview

  The Uplink College Database is a structured Relational Database Management System (RDBMS) designed to efficiently store and manage student enrollments, courses, instructors, and academic records. The project implements SQL to design, populate, and analyze data for an   
  educational institution.

📌 Objectives
  1. Track student information (personal details, enrollment status, GPA).
  2. Manage course details (course codes, names, levels, assigned instructors).
  3. Store instructor information (contact details, experience, and courses taught).
  4. Maintain academic records (grades, enrollments, and course performance).
  5. Generate analytical reports using SQL queries, including:
      - Student enrollment trends.
      - Instructor workloads.
      - Course popularity.
      - Academic performance evaluations.

**2️⃣ Database Design and Implementation**

📌 Database Schema

  The database follows 3rd Normal Form (3NF) to eliminate redundancy and improve efficiency.

🔹 Tables & Relationships
  1. Students (*StudentID* as PK)
  2. Instructors (*InstructorID* as PK)
  3. Courses (*CourseID* as PK, FK to Instructors)
  4. Enrollments (*EnrollmentID* as PK, FK to Students and Courses)
  5. Grades (*GradeID* as PK, FK to Students and Courses)


# 3️⃣ **Queries**

**🟢 1. Selecting Data**

1. Retrieve the student IDs and names of all enrolled students.

    ```
    SELECT StudentID, FirstName + ' ' + LastName AS FullName 
    FROM Students 
    WHERE EnrollmentStatus = 'Active';
    ```
    <img width="338" alt="image" src="https://github.com/user-attachments/assets/cf837a95-4389-4688-9b82-03b8ba5c9acd" />

    ```
    -- Using CTE
    WITH EnrolledStudents AS (
        SELECT StudentID, FirstName + ' ' + LastName AS FullName
      FROM Students
      WHERE EnrollmentStatus = 'Active'
    )
    SELECT * FROM EnrolledStudents;
    ```
    <img width="342" alt="image" src="https://github.com/user-attachments/assets/46b022ab-c546-47e1-b726-365dca22dd62" />

2.	Get the course codes and names of all available courses.

     ```
    SELECT courseCode, CourseName
    FROM Courses;
    ```
    <img width="360" alt="image" src="https://github.com/user-attachments/assets/ada1f6b0-eb37-48c8-8a00-9fc7aeca9978" />


3.	Fetch the instructor IDs and names of all instructors teaching courses.
   
     ```
     -- Option 1
    SELECT DISTINCT i.InstructorID, i.FirstName + ' ' + i.LastName AS FullName 
    FROM Instructors i
    JOIN Courses c ON i.InstructorID = c.InstructorID;
    ```

   ```
     -- Using CTEs
    WITH InstructorTeaching AS (
        SELECT DISTINCT i.InstructorID, i.FirstName + ' ' + i.LastName AS FullName
    FROM Instructors i
    JOIN Courses c ON i.InstructorID = c.InstructorID
    )
    SELECT * FROM InstructorTeaching;
  ```

  <img width="305" alt="image" src="https://github.com/user-attachments/assets/be2a3001-ff40-4744-8b97-d675c51ee2cd" />

6.	Retrieve the student IDs and course codes for all enrolled courses.
7.	Get the grades and corresponding course codes for all students.

   
**🟠 2. Filtering Data**

7. Retrieve the student IDs and names of students enrolled in courses with 'Advanced' in their course names.
8.	Get the course codes and names of courses taught by instructors with more than 5 years of teaching experience.
9.	Fetch the student IDs and names of students who have enrolled in more than 3 courses.
10.	Retrieve the instructor IDs and names of instructors teaching courses with more than 30 students enrolled.
11.	Get the grades and corresponding course codes for students with a GPA greater than 3.5.
🔵 3. Sorting Data
1.	Retrieve the student IDs and names of all enrolled students, sorted alphabetically by student names.
2.	Get the course codes and names of all available courses, sorted alphabetically by course codes.
3.	Fetch the instructor IDs and names of all instructors teaching courses, sorted alphabetically by instructor names.
4.	Retrieve the student IDs and course codes for all enrolled courses, sorted in ascending order of student IDs.
5.	Get the grades and corresponding course codes for all students, sorted in descending order of grades.
   
**🟣 4. Aggregation & Analytical Queries**
1.	Retrieve distinct course levels available in the course offerings.
2.	Get distinct student IDs for all enrolled students.
3.	Fetch distinct instructor IDs for all instructors.
4.	Retrieve distinct course codes for all available courses.
5.	Get distinct grades for all students.

**4️⃣ Key Findings**

Most enrolled courses: [Course Name] has the highest enrollments.
Top-performing students: [Student Name] achieved a GPA of 4.0.
Instructors with the highest workload: [Instructor Name] manages X students.
Enrollment trends: Advanced courses have higher enrollments.

**5️⃣ Conclusion**

The Uplink College Database efficiently stores, retrieves, and analyzes student academic records, enrollments, instructor workloads, and course performance.

By using SQL functions, CTEs, and Window Functions, the project:

Optimizes data retrieval.
Reduces redundancy.
Provides insightful analytics for academic decision-making.

**6️⃣ Recommendations**

Automate Data Entry: Use stored procedures or Python scripts to prevent missing records.
Enhance Reporting: Integrate Power BI/Tableau for dynamic dashboards.
Optimize Performance: Add indexes on frequently queried fields (StudentID, CourseID).
Future Expansion: Include attendance tracking and student feedback analysis.




























