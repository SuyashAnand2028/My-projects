# My-projects
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_STUDENTS 100
#define MAX_COURSES 50
#define MAX_ENROLLMENTS 200

typedef struct {
    int id;
    char name[100];
    int age;
    char department[50];
} Student;

typedef struct {
    int id;
    char name[100];
    int credits;
} Course;

typedef struct {
    int studentId;
    int courseId;
} Enrollment;

Student students[MAX_STUDENTS];
Course courses[MAX_COURSES];
Enrollment enrollments[MAX_ENROLLMENTS];

int studentCount = 0;
int courseCount = 0;
int enrollmentCount = 0;

void addStudent() {
    if (studentCount >= MAX_STUDENTS) {
        printf("Maximum number of students reached!\n");
        return;
    }

    students[studentCount].id = studentCount + 1;
    printf("Enter student name: ");
    scanf(" %[^\n]", students[studentCount].name);
    printf("Enter student age: ");
    scanf("%d", &students[studentCount].age);
    printf("Enter student department: ");
    scanf(" %[^\n]", students[studentCount].department);

    studentCount++;
    printf("Student added successfully!\n");
}

void viewStudents() {
    if (studentCount == 0) {
        printf("No students available.\n");
        return;
    }

    for (int i = 0; i < studentCount; i++) {
        printf("Student ID: %d\n", students[i].id);
        printf("Name: %s\n", students[i].name);
        printf("Age: %d\n", students[i].age);
        printf("Department: %s\n", students[i].department);
        printf("-------------------------\n");
    }
}

void updateStudent() {
    int id;
    printf("Enter student ID to update: ");
    scanf("%d", &id);

    for (int i = 0; i < studentCount; i++) {
        if (students[i].id == id) {
            printf("Enter new name: ");
            scanf(" %[^\n]", students[i].name);
            printf("Enter new age: ");
            scanf("%d", &students[i].age);
            printf("Enter new department: ");
            scanf(" %[^\n]", students[i].department);
            printf("Student updated successfully!\n");
            return;
        }
    }

    printf("Student not found.\n");
}

void deleteStudent() {
    int id;
    printf("Enter student ID to delete: ");
    scanf("%d", &id);

    for (int i = 0; i < studentCount; i++) {
        if (students[i].id == id) {
            for (int j = i; j < studentCount - 1; j++) {
                students[j] = students[j + 1];
            }
            studentCount--;
            printf("Student deleted successfully!\n");
            return;
        }
    }

    printf("Student not found.\n");
}

void addCourse() {
    if (courseCount >= MAX_COURSES) {
        printf("Maximum number of courses reached!\n");
        return;
    }

    courses[courseCount].id = courseCount + 1;
    printf("Enter course name: ");
    scanf(" %[^\n]", courses[courseCount].name);
    printf("Enter course credits: ");
    scanf("%d", &courses[courseCount].credits);

    courseCount++;
    printf("Course added successfully!\n");
}

void viewCourses() {
    if (courseCount == 0) {
        printf("No courses available.\n");
        return;
    }

    for (int i = 0; i < courseCount; i++) {
        printf("Course ID: %d\n", courses[i].id);
        printf("Name: %s\n", courses[i].name);
        printf("Credits: %d\n", courses[i].credits);
        printf("-------------------------\n");
    }
}

void updateCourse() {
    int id;
    printf("Enter course ID to update: ");
    scanf("%d", &id);

    for (int i = 0; i < courseCount; i++) {
        if (courses[i].id == id) {
            printf("Enter new name: ");
            scanf(" %[^\n]", courses[i].name);
            printf("Enter new credits: ");
            scanf("%d", &courses[i].credits);
            printf("Course updated successfully!\n");
            return;
        }
    }

    printf("Course not found.\n");
}

void deleteCourse() {
    int id;
    printf("Enter course ID to delete: ");
    scanf("%d", &id);

    for (int i = 0; i < courseCount; i++) {
        if (courses[i].id == id) {
            for (int j = i; j < courseCount - 1; j++) {
                courses[j] = courses[j + 1];
            }
            courseCount--;
            printf("Course deleted successfully!\n");
            return;
        }
    }

    printf("Course not found.\n");
}

void enrollStudent() {
    if (enrollmentCount >= MAX_ENROLLMENTS) {
        printf("Maximum number of enrollments reached!\n");
        return;
    }

    int studentId, courseId;
    printf("Enter student ID: ");
    scanf("%d", &studentId);
    printf("Enter course ID: ");
    scanf("%d", &courseId);

    enrollments[enrollmentCount].studentId = studentId;
    enrollments[enrollmentCount].courseId = courseId;
    enrollmentCount++;
    printf("Student enrolled in course successfully!\n");
}

void viewEnrollments() {
    if (enrollmentCount == 0) {
        printf("No enrollments available.\n");
        return;
    }

    for (int i = 0; i < enrollmentCount; i++) {
        printf("Enrollment %d:\n", i + 1);
        printf("  Student ID: %d\n", enrollments[i].studentId);
        printf("  Course ID: %d\n", enrollments[i].courseId);
        printf("-------------------------\n");
    }
}

void displayMenu() {
    printf("\nCollege Management System\n");
    printf("1. Add Student\n");
    printf("2. View Students\n");
    printf("3. Update Student\n");
    printf("4. Delete Student\n");
    printf("5. Add Course\n");
    printf("6. View Courses\n");
    printf("7. Update Course\n");
    printf("8. Delete Course\n");
    printf("9. Enroll Student\n");
    printf("10. View Enrollments\n");
    printf("11. Exit\n");
    printf("Enter your choice: ");
}

int main() {
    int choice;

    while (1) {
        displayMenu();
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addStudent();
                break;
            case 2:
                viewStudents();
                break;
            case 3:
                updateStudent();
                break;
            case 4:
                deleteStudent();
                break;
            case 5:
                addCourse();
                break;
            case 6:
                viewCourses();
                break;
            case 7:
                updateCourse();
                break;
            case 8:
                deleteCourse();
                break;
            case 9:
                enrollStudent();
                break;
            case 10:
                viewEnrollments();
                break;
            case 11:
                return 0;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }

    return 0;
}
