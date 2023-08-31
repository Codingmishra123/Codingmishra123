#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct person {
    int id;
    char *name;
    int age;
    int height;
    int weight;
};
void swap(struct person *a, struct person *b) {
    struct person temp = *a;
    *a = *b;
    *b = temp;
}
void minHeapifyAge(struct person *arr, int n, int i) {
    int smallest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && arr[left].age < arr[smallest].age)
        smallest = left;

    if (right < n && arr[right].age < arr[smallest].age)
        smallest = right;

    if (smallest != i) {
        swap(&arr[i], &arr[smallest]);
        minHeapifyAge(arr, n, smallest);
    }
}


void maxHeapifyWeight(struct person *arr, int n, int i) {
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && arr[left].weight > arr[largest].weight)
        largest = left;

    if (right < n && arr[right].weight > arr[largest].weight)
        largest = right;

    if (largest != i) {
        swap(&arr[i], &arr[largest]);
        maxHeapifyWeight(arr, n, largest);
    }
}

int main() {
    int option, n;
    struct person *persons = NULL;

    do {
        printf("\nMAIN MENU (HEAP)\n");
        printf("1. Read Data\n");
        printf("2. Create a Min-heap based on the age\n");
        printf("3. Create a Max-heap based on the weight\n");
        printf("4. Display weight of the youngest person\n");
        printf("5. Insert a new person into the Min-heap\n");
        printf("6. Delete the oldest person\n");
        printf("7. Exit\n");
        printf("\nEnter option: ");
        scanf("%d", &option);

        switch (option) {
            case 1:

                n = 7; 
                persons = (struct person *)malloc(n * sizeof(struct person));

                break;
            case 2:                
                for (int i = n / 2 - 1; i >= 0; i--)          
                    minHeapifyAge(persons, n, i);
                printf("Min-heap based on age created.\n");
                break;

            case 3:
                for (int i = n / 2 - 1; i >= 0; i--)
                    maxHeapifyWeight(persons, n, i);
                printf("Max-heap based on weight created.\n");
                break;

            case 4:
                printf("Weight of youngest student: %.2f kg\n", persons[0].weight);
                break;

            case 5:
                break;

            case 6:
                break;

            case 7:
                printf("Exiting...\n");
                break;

            default:
                printf("Invalid option. Please choose a valid option.\n");
        }

    } 
    while (option != 7);

    return 0;
}
- 👋 Hi, I’m @Codingmishra123
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Codingmishra123/Codingmishra123 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
