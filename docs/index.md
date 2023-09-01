# Data Manipulation and Management

5:30-6:50 PM – Jubel 120
Fall 2023

Instructor:
Ty Schlichenmeyer
<t.schlic@wustl.edu>

TAs:

- Siming Yin, <siming@wustl.edu>
- Levi Kaster, <k.levi@wustl.edu>
- Lavinia Xu, <lavinia.x@wustl.edu>

## Office Hours

Professor (virtual): Fridays 12PM

Zoom link posted on Canvas

TAs: TBD

## Department Course Description

_At the base of data science, data needs to be acquired, integrated and preprocessed. This important step in the data science workflow ensures both quantity and quality of data and improves the effectiveness of the following steps of data processing. Students will gain an understanding of concepts and approaches of data acquisition and governance including data shaping, information extraction, information integration, data reduction and compression, data transformation as well as data cleaning. The course will further highlight the ethical responsibility of protecting the integrity of data and proper use of data._

### Prerequisites

- CSE 131: Introduction to Computer Science
- CSE 217A: Introduction to Data Science
- Corequisite- CSE 247: Data Structures and Algorithms

> Note: These are Department-Listed Pre- and Co-requisites with various degrees of applicability. Talk to me if you have concerns or questions.

## Course Objectives

Students should leave this course with an understanding of common data storage/organization patterns and pipeline structures using modern software tools and  engineering techniques:

- Tabular/relational data (SQL, Pandas) and document-based data (JSON, etc).
- Data reshaping and aggregation
- Data Cleaning and Normalization
- Collecting data from APIs and web scraping
- ETL and data pipelines
- Feeding data to interactive dashboards
- File and Project management techniques
- Collaborating on software projects

Introductory-level experience and comfort with programming is expected coming into this course. The course be primarily be taught in Python and secondarily will introduce database querying languages. Previous experience with Python will be helpful but not necessary.

Students leaving this course will have firsthand experience with industry skills and tools such as testing, documentation, version control/git, containerization, and user requirements.

## Course Materials and Communications

### Website

Course materials will be hosted on our course website:

<https://wustl-data.github.io/fl23>

The website will contain:

- The course schedule
- Introductory material, interactive exercises, and lecture slides
- Assignment instructions
- Links to important course webpages (e.g. GitHub, Canvas)
- External Resources
- A web-friendly copy of this syllabus

### Canvas

Lecture slides, grades, and urgent announcements will be posted on Canvas.

### GitHub

All students must create a GitHub account using their WUSTL email. They will be added to the course's [GitHub Organization](https://github.com/wustl-data).

- Assignments will be posted as branches on the [course repository](https://github.com/wustl-data/fl23).
- Students will submit assignments by pushing code to GitHub, where GitHub Actions will automatically grade the assignment.
- Class discussion, including questions for homework help, project help, and course logistics, will happen on [GitHub Discussions](https://github.com/orgs/wustl-data/discussions).

## Grades

### **Assignments**: 50%

- You will be be given 6 programming assignments totaling 50 points (making them worth roughly 8 points each)
- Most, if not all, homeworks will be autograded.
- The autograder will accept unlimited submissions up to the deadline.
- Your lowest assignment grade will be dropped.

### **Projects**: 40%

- Students must submit a team project utilizing course material. A final submission will be due on December 19th, 2023. There will be 3 progress checkpoints during the semester at which each group will be responsible for submitting a progress report and code samples.

  - 10%: Progress Report 1
  - 10%: Progress Report 2
  - 10%: Progress Report 3
  - 5%: Final group presentation
  - 5%: Final code evaluation

Rubrics for each of these submissions will be provided, and will include peer evaluation surveys or other measures to ensure equitable distribution of work.

#### Late Submission Policy

Incomplete or unfinished work may be resubmitted up to **two full weeks** after the deadline for 50% credit _in addition to any credit earned before the deadline_.

### **Class Participation**: 10%

- 5% - Completion of in-class programming exercises.
- 5% - Attendance on in-class team collaboration days.

It will not be announced before class if there will be an in-class exercise assigned or not.

#### Excused Absences

Students with _excused absences_ will be able to submit the exercise on their own before midnight the same day or a time agreed upon with the instructor. For group participation days, excused absences should be made up with work agreed on by your teammates. Clearance for excused absences must be obtained from the instructor via email before the class period.

## Class Structure

On most days, class will begin with 30-45 minutes of lecture. The remaining class time will be spent working on in-class exercises related to the material. You will work on the exercises in randomly assigned pairs.

Periodically throughout the semester, we will have team collaboration days where you will work on your team project. You will be provided with suggested exercises but are ultimately free to use this time how you see fit.

## Course Policy on Academic Integrity

Coding assignments must represent your own work. You may discuss high-level approaches to problems with your classmates, but you MUST acknowledge your collaborators in the README of your submitted assignment. Do not otherwise copy, borrow, or share coding implementations of your work on these assignments. Departmental and University Academic Integrity policies are outlined further on the course website.

This course places no restrictions on the usage of AI-based IDE assistant tools such as GitHub CoPilot or LLMs such as ChatGPT. Students are encouraged to do their own research on AI ethics and act in accordance with usage agreements and university policies.

## Lecture recordings

To accommodate COVID isolation procedures and other considerations, lectures will be recorded on Zoom for most class sessions, however, access to these streams/recordings will be restricted to “upon-request” to encourage class attendance.

## University Policies and Resources

The following University Policies and resources are detailed on our course website:

- Preferred Name and Personal Pronouns - <https://wustl-data.github.io/syllabus/pronouns>
- COVID-19 Health and Safety Protocol - <https://wustl-data.github.io/syllabus/covid>
- Disability & Religious Accommodations - <https://wustl-data.github.io/syllabus/disability-religious>
- Other resources - <https://wustl-data.github.io/syllabus/resources>

## Course Schedule

The course schedule is provided below and is _subject to change throughout the semester_. The most up to date version may usually be found on the course website.

While the course registration page lists a final exam date, we will not be having a final exam. The final project will be due on this day instead.

> Note: This version of the course schedule is a copy from last semester and will be updated the first week of class to reflect changes.

| Week | Day | Date   | Topic                                 | Assignment | Lecture | Project Stage |
| ---- | --- | ------ | ------------------------------------- | ---------- | ------- | ------------- |
| 1    | Tu  |  | Course Overview and Syllabus          |            | 1       |               |
|      | Th  |  | Data transformation basics            |            | 2       | 1             |
| 2    | Tu  |  | Python and Pandas                     |            | 3       | 1             |
|      | Th  |   | Data engineering basics               |            | 4       | 1             |
| 3    | Tu  |   | Group Collaboration Day               |            |         | 1             |
|      | Th  |   | Fetching data from web APIs           | 1          | 5       | 1             |
| 4    | Tu  |  | Web crawling basics                   |            | 6       | 1             |
|      | Th  |  | Deep data cleaning                    |            | 7       | 1             |
| 5    | Tu  |  | Data normalization                    | 2          | 8       | 1             |
|      | Th  |  | Group Collaboration                   |            |         | 1             |
| 6    | Tu  |  | ETL and Data Warehousing              |            | 9       | 2             |
|      | Th  |   | The dbt framework                     | 3          | 10      | 2             |
| 7    | Tu  |   | Test-Driven Data                      |            | 11      | 2             |
|      | Th  |   | Great Expectations                    | 4          | 12      | 2             |
| 9    | Tu  |  | Group Collaboration                   |            |         | 2             |
|      | Th  |  | Data Orchestration and large datasets |            | 13      | 2             |
| 10   | Tu  |  | Basics of SQL, NoSQL, and GraphQL     | 5          | 14      | 2             |
|      | Th  |  | Database Migrations & SQL Tuning      |            | 15      | 2             |
| 11   | Tu  |   | Group Collaboration                   |            |         | 2             |
|      | Th  |   | Generating Plots and Docs             | 6          | 16      | 3             |
| 12   | Tu  |  | Data Dashboards                       |            | 17      | 3             |
|      | Th  |  | Geospatial Data                       |            | 18      | 3             |
| 13   | Tu  |  | Multidimensional and time-series data |           | 19      | 3             |
|      | Th  |  | Group Collaboration                   |            |         | 3             |
| 14   | Tu  |  | Group Presentations                   |            |         |               |
|      | Th  |  | Group Presentations                   |            |         |               |
|      | Tu  |   | Final Project Due                     |            |         |               |
