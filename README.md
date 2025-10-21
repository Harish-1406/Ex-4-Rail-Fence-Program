# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.

STEP-2: Arrange the plain text in row columnar matrix format.

STEP-3: Now read the keyword depending on the number of columns of the plain text.

STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.

STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```c
#include <stdio.h>
#include <string.h>

int main() {
    char plain[1024], cipher[1024];
    int rails, len, i, j, row, col;
    printf("Enter Plaintext: ");
    fgets(plain, sizeof plain, stdin);
    if (plain[strlen(plain)-1] == '\n') plain[strlen(plain)-1] = '\0';
    len = strlen(plain);
    printf("Enter number of rails: ");
    scanf("%d", &rails);

    int mark[rails][len];
    for (i = 0; i < rails; i++)
        for (j = 0; j < len; j++)
            mark[i][j] = 0;

    row = 0;
    int down = 1;
    for (i = 0; i < len; i++) {
        mark[row][i] = 1;
        if (down) {
            if (row == rails - 1) { down = 0; row--; }
            else row++;
        } else {
            if (row == 0) { down = 1; row++; }
            else row--;
        }
    }

    int k = 0;
    for (i = 0; i < rails; i++)
        for (j = 0; j < len; j++)
            if (mark[i][j] == 1)
                cipher[k++] = plain[j];
    cipher[k] = '\0';

    printf("Ciphertext: %s\n", cipher);
    return 0;
}
```
# OUTPUT

<img width="462" height="238" alt="image" src="https://github.com/user-attachments/assets/fb8b33b5-df84-4082-a505-336baada0376" />

# RESULT
Successfully implemented a C program for the rail fence transposition technique.
