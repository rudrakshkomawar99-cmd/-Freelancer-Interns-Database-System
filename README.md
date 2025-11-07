# -Freelancer-Interns-Database-System
This project is made by using C language's concept like loops, conditional statement, structures, bubble sort, etc. The concept of this project is to make a database for companies to keep track of the freelancers and interns working for them and if a individual is good and has reached a specific requirement then they are eligible for job in company

#include <stdio.h>

struct person {
    char name[50];
    int projects;
    int stipend;
};

void bubbleSort(struct person arr[], int n) {
    int i, j;
    struct person temp;
    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - i - 1; j++) {
            if (arr[j].stipend > arr[j + 1].stipend) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

int isEligible(struct person p) {
    if (p.projects >= 3 && p.stipend >= 5000)
        return 1;
    else
        return 0;
}

void inputData(struct person arr[], int n, char typeName[]) {
    int i;
    printf("\n--- Enter details for %s ---\n", typeName);
    for (i = 0; i < n; i++) {
        printf("\nName: ");
        scanf("%s", arr[i].name);
        printf("Projects assigned: ");
        scanf("%d", &arr[i].projects);
        printf("Stipend: ");
        scanf("%d", &arr[i].stipend);
    }
}

void displayData(struct person arr[], int n, char typeName[]) {
    int i;
    printf("\n===== Sorted %s (By Stipend - Ascending) =====\n", typeName);
    for (i = 0; i < n; i++) {
        printf("Name: %s | Projects: %d | Stipend: %d | %s\n",
               arr[i].name,
               arr[i].projects,
               arr[i].stipend,
               isEligible(arr[i]) ? "Eligible " : "Not Eligible ");
    }
}

int main() {
    int nf, ni;

    printf("------ FREELANCER & INTERN DATABASE SYSTEM ------\n");

    printf("\nEnter number of freelancers: ");
    scanf("%d", &nf);
    struct person freelancers[nf];
    inputData(freelancers, nf, "Freelancers");
    bubbleSort(freelancers, nf);

    printf("\nEnter number of interns: ");
    scanf("%d", &ni);
    struct person interns[ni];
    inputData(interns, ni, "Interns");
    bubbleSort(interns, ni);

    displayData(freelancers, nf, "Freelancers");
    displayData(interns, ni, "Interns");

    return 0;
}

