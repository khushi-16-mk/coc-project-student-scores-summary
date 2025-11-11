# coc-project-student-scores-summary
This project calculates the average, highest, and lowest grades of students from user input. It demonstrates basic C programming techniques such as arrays, loops, and file handling. The program also uses simple mathematical operations like mean and percentage calculations to analyze student performance.
The concepts of C has been used as follows:- C Concepts:
Variables and Data Types
for and while loops
Arrays
Functions

Maths Concepts:
Mean (Average)
Minimum and Maximum values
Percentage calculation

/* Student Score Analyzer
   - Reads n scores into a 1D array
   - Computes mean (average), highest, and lowest using separate functions
   - Displays a clean summary report
*/

#include <stdio.h>
#include <stdlib.h>

/* Function to calculate the average (mean) of the scores */
double mean(const int *arr, int size) {
    long long sum = 0;
    for (int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return sum / (double)size;  // Convert to double for accurate decimal average
}

/* Function to find the highest score */
int highest(const int *arr, int size) {
    int max = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}

/* Function to find the lowest score */
int lowest(const int *arr, int size) {
    int min = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] < min) {
            min = arr[i];
        }
    }
    return min;
}

int main(void) {
    int n;

    printf("How many student scores will you enter? ");
    if (scanf("%d", &n) != 1 || n <= 0) {
        printf("Invalid input. Please enter a positive integer.\n");
        return 1;
    }

    /* Allocate memory dynamically for scores */
    int *scores = (int *)malloc(n * sizeof(int));
    if (scores == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    /* Read scores */
    for (int i = 0; i < n; i++) {
        printf("Enter score for student %d: ", i + 1);
        if (scanf("%d", &scores[i]) != 1) {
            printf("Invalid input. Please enter integers only.\n");
            free(scores);
            return 1;
        }
    }

    /* Analysis */
    double avg = mean(scores, n);
    int hi = highest(scores, n);
    int lo = lowest(scores, n);

    /* Display summary report */
    printf("\n--- Class Quiz Report ---\n");
    printf("Class Average: %.1f\n", avg);
    printf("Highest Score: %d\n", hi);
    printf("Lowest Score: %d\n", lo);

    /* Free allocated memory */
    free(scores);

    return 0;
}
