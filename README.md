#include <stdio.h>

#define MAX 10  // Maximum size of matrix (you can adjust the size)

void multiplyMatrices(int firstMatrix[MAX][MAX], int secondMatrix[MAX][MAX], int result[MAX][MAX], int rowFirst, int colFirst, int rowSecond, int colSecond) {
    // Initialize the result matrix with 0
    for (int i = 0; i < rowFirst; i++) {
        for (int j = 0; j < colSecond; j++) {
            result[i][j] = 0;
        }
    }

    // Multiply the matrices
    for (int i = 0; i < rowFirst; i++) {
        for (int j = 0; j < colSecond; j++) {
            for (int k = 0; k < colFirst; k++) {
                result[i][j] += firstMatrix[i][k] * secondMatrix[k][j];
            }
        }
    }
}

void printMatrix(int matrix[MAX][MAX], int row, int col) {
    for (int i = 0; i < row; i++) {
        for (int j = 0; j < col; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
}

int main() {
    int firstMatrix[MAX][MAX], secondMatrix[MAX][MAX], result[MAX][MAX];
    int rowFirst, colFirst, rowSecond, colSecond;

    // Get the dimensions of the first matrix
    printf("Enter rows and columns for the first matrix: ");
    scanf("%d %d", &rowFirst, &colFirst);

    // Get the elements of the first matrix
    printf("Enter elements of matrix 1:\n");
    for (int i = 0; i < rowFirst; i++) {
        for (int j = 0; j < colFirst; j++) {
            printf("Enter element [%d][%d]: ", i + 1, j + 1);
            scanf("%d", &firstMatrix[i][j]);
        }
    }

    // Get the dimensions of the second matrix
    printf("Enter rows and columns for the second matrix: ");
    scanf("%d %d", &rowSecond, &colSecond);

    // Check if multiplication is possible
    if (colFirst != rowSecond) {
        printf("Matrix multiplication not possible. Columns of first matrix must equal rows of second matrix.\n");
        return 0;
    }

    // Get the elements of the second matrix
    printf("Enter elements of matrix 2:\n");
    for (int i = 0; i < rowSecond; i++) {
        for (int j = 0; j < colSecond; j++) {
            printf("Enter element [%d][%d]: ", i + 1, j + 1);
            scanf("%d", &secondMatrix[i][j]);
        }
    }

    // Call the multiplyMatrices function
    multiplyMatrices(firstMatrix, secondMatrix, result, rowFirst, colFirst, rowSecond, colSecond);

    // Display the result
    printf("Resultant Matrix after multiplication:\n");
    printMatrix(result, rowFirst, colSecond);

    return 0;
}
