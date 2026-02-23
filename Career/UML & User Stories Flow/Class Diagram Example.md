---
tags:
  - UML
  - OOP
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses a class diagram based on the user stories for a driving school.
Status: Final
Started: 
EditDate: 2024-02-20
Relates: "[[Epics to user stories]]"
dg-publish:
---
## Administrator Table
| Field | Type |
| ---- | ---- |
| username | VARCHAR |
| password | VARCHAR |
|  |  |
| login() | Method |
| addInstructor | Method |
| addCurriculum | Method |
| scheduleClass | Method |


## Instructor Table
| Field | Type |
| ---- | ---- |
| instructorId | INT |
| name | VARCHAR |
|  |  |
| login() | Method |
| viewSchedule | Method |
| conductLesson | Method |
| teachDefensiveDriving | Method |


## Student Table
| Field | Type |
| ---- | ---- |
| studentId | INT |
| name | VARCHAR |
|  |  |
| login() | Method |
| viewSchedule | Method |
| enrollInCourse | Method |


## Curriculum Table
| Field | Type |
| ---- | ---- |
| curriculumId | INT |
| name | VARCHAR |
|  |  |
| createCurriculum() | Method |
| updateCurriculum() | Method |
| deleteCurriculum() | Method |
| getCurriculum() | Method |


## Lesson Table
| Field | Type |
| ---- | ---- |
| lessonId | INT |
| title | VARCHAR |
| description | VARCHAR |
| instructorId | INT |
|  |  |
| createLesson() | Method |
| updateLesson() | Method |
| deleteLesson() | Method |
| getLesson() | Method |


**Schedule Table:**

| Field | Type |
| ---- | ---- |
| scheduleId | INT |
| date | DATE |
| time | TIME |
| lessonId | INT |
|  |  |
| createSchedule() | Method |
| updateSchedule() | Method |
| deleteSchedule() | Method |
| getSchedule() | Method |

This class diagram represents the key entities and their relationships in the driving school system. The driving school administrator, instructor, and student are depicted as separate classes. The administrator class has attributes like username and password, while the instructor class has an additional attribute, instructorId. The student class has attributes like studentId and name.

The administrator class has methods such as login(), addInstructor(), addCurriculum(), and scheduleClass(). The instructor class has methods like login(), viewSchedule(), conductLesson(), and teachDefensiveDriving(). The student class has methods like login(), viewSchedule(), and enrollInCourse().

There are additional classes representing the curriculum, lesson, and schedule. The curriculum class has attributes like curriculumId and name, and methods such as createCurriculum(), updateCurriculum(), deleteCurriculum(), and getCurriculum(). The lesson class has attributes like lessonId, title, description, and instructorId, and methods such as createLesson(), updateLesson(), deleteLesson(), and getLesson(). The schedule class has attributes like scheduleId, date, time, and lessonId, and methods such as createSchedule(), updateSchedule(), deleteSchedule(), and getSchedule().

This class diagram provides an overview of the entities involved in the driving school system and their relationships. It serves as a foundation for understanding the system's structure and can be used as a starting point for further development and implementation.



## Code Implementation

```java
// Administrator class
public class Administrator {
    private String username;
    private String password;
    
    public Administrator(String username, String password) {
        this.username = username;
        this.password = password;
    }
    
    public void login() {
        // Login logic
    }
    
    public void addInstructor(Instructor instructor) {
        // Add instructor logic
    }
    
    public void addCurriculum(Curriculum curriculum) {
        // Add curriculum logic
    }
    
    public void scheduleClass(Schedule schedule) {
        // Schedule class logic
    }
}

// Instructor class
public class Instructor {
    private String instructorId;
    private String name;
    
    public Instructor(String instructorId, String name) {
        this.instructorId = instructorId;
        this.name = name;
    }
    
    public void login() {
        // Login logic
    }
    
    public void viewSchedule() {
        // View schedule logic
    }
    
    public void conductLesson(Lesson lesson) {
        // Conduct lesson logic
    }
    
    public void teachDefensiveDriving() {
        // Teach defensive driving logic
    }
}

// Student class
public class Student {
    private String studentId;
    private String name;
    
    public Student(String studentId, String name) {
        this.studentId = studentId;
        this.name = name;
    }
    
    public void login() {
        // Login logic
    }
    
    public void viewSchedule() {
        // View schedule logic
    }
    
    public void enrollInCourse(Curriculum curriculum) {
        // Enroll in course logic
    }
}

// Curriculum class
public class Curriculum {
    private String curriculumId;
    private String name;
    
    public Curriculum(String curriculumId, String name) {
        this.curriculumId = curriculumId;
        this.name = name;
    }
    
    public void createCurriculum() {
        // Create curriculum logic
    }
    
    public void updateCurriculum() {
        // Update curriculum logic
    }
    
    public void deleteCurriculum() {
        // Delete curriculum logic
    }
    
    public void getCurriculum() {
        // Get curriculum logic
    }
}

// Lesson class
public class Lesson {
    private String lessonId;
    private String title;
    private String description;
    private String instructorId;
    
    public Lesson(String lessonId, String title, String description, String instructorId) {
        this.lessonId = lessonId;
        this.title = title;
        this.description = description;
        this.instructorId = instructorId;
    }
    
    public void createLesson() {
        // Create lesson logic
    }
    
    public void updateLesson() {
        // Update lesson logic
    }
    
    public void deleteLesson() {
        // Delete lesson logic
    }
    
    public void getLesson() {
        // Get lesson logic
    }
}

// Schedule class
public class Schedule {
    private String scheduleId;
    private Date date;
    private Time time;
    private String lessonId;
    
    public Schedule(String scheduleId, Date date, Time time, String lessonId) {
        this.scheduleId = scheduleId;
        this.date = date;
        this.time = time;
        this.lessonId = lessonId;
    }
    
    public void createSchedule() {
        // Create schedule logic
    }
    
    public void updateSchedule() {
        // Update schedule logic
    }
    
    public void deleteSchedule() {
        // Delete schedule logic
    }
    
    public void getSchedule() {
        // Get schedule logic
    }


}
```

