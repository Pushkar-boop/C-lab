7. An array of record contains information of managers and workers of a company. Print all the data  
of managers and workers in separate files

//program 

#include <stdio.h>
#include <string.h>

// Structure to store employee data
struct Employee {
    char name[50];
    char role[10]; // Manager or Worker
    int age;
    float salary;
};

int main() {
    int n, i;

    // Array to store multiple employees
    struct Employee emp[100];

    // Input number of employees
    printf("Enter the number of employees: ");
    scanf("%d", &n);

    // Input employee details
    for (i = 0; i < n; i++) {
        printf("\nEnter details for employee %d:\n", i + 1);
        printf("Name: ");
        scanf("%s", emp[i].name);
        printf("Role (Manager/Worker): ");
        scanf("%s", emp[i].role);
        printf("Age: ");
        scanf("%d", &emp[i].age);
        printf("Salary: ");
        scanf("%f", &emp[i].salary);
    }

    // Open files to write data
    FILE *managerFile = fopen("managers.txt", "w");
    FILE *workerFile = fopen("workers.txt", "w");

    // Check if files opened successfully
    if (managerFile == NULL || workerFile == NULL) {
        printf("Error opening file!\n");
        return 1;
    }

    // Separate and write data to respective files
    for (i = 0; i < n; i++) {
        if (strcmp(emp[i].role, "Manager") == 0 || strcmp(emp[i].role, "manager") == 0) {
            fprintf(managerFile, "Name: %s\nAge: %d\nSalary: %.2f\n\n", emp[i].name, emp[i].age, emp[i].salary);
        } 
        else if (strcmp(emp[i].role, "Worker") == 0 || strcmp(emp[i].role, "worker") == 0) {
            fprintf(workerFile, "Name: %s\nAge: %d\nSalary: %.2f\n\n", emp[i].name, emp[i].age, emp[i].salary);
        }
    }

    // Close files
    fclose(managerFile);
    fclose(workerFile);

    printf("\nData successfully written to managers.txt and workers.txt.\n");

    return 0;
}



//Input 

Enter the number of employees: 3

Enter details for employee 1:
Name: John
Role (Manager/Worker): Manager
Age: 35
Salary: 75000

Enter details for employee 2:
Name: Mike
Role (Manager/Worker): Worker
Age: 28
Salary: 30000

Enter details for employee 3:
Name: Sarah
Role (Manager/Worker): Worker
Age: 25
Salary: 28000


//output 
//managers.txt 
Name: John
Age: 35
Salary: 75000.00

//workers.txt
Name: Mike
Age: 28
Salary: 30000.00

Name: Sarah
Age: 25
Salary: 28000.00
