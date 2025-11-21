
#include <stdio.h>

struct Employee {
    char name[50];
    int id;
    int stipend;
};

void bubbleSort(struct Employee arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j].stipend > arr[j + 1].stipend) {
                // Swap
                struct Employee temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

int main() {
    int n;

    printf("Enter number of employees: ");
    scanf("%d", &n);

    struct Employee emp[n];

    // Input
    for (int i = 0; i < n; i++) {
        printf("\nEnter name of employee %d: ", i + 1);
        scanf("%s", emp[i].name);

        printf("Enter ID: ");
        scanf("%d", &emp[i].id);

        printf("Enter stipend: ");
        scanf("%d", &emp[i].stipend);
    }

    // Sort employees by stipend
    bubbleSort(emp, n);

    printf("\n--- Employees Sorted by Stipend ---\n");
    for (int i = 0; i < n; i++) {
        printf("Name: %s  |  ID: %d  |  Stipend: %d\n",
               emp[i].name, emp[i].id, emp[i].stipend);
    }

    return 0;
}


