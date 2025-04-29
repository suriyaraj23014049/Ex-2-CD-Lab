# Ex-2-GENERATION OF LEXICAL TOKENS LEX FLEX TOOL
# Name:SURIYA RAJ K
# Reg no:212223040216
# Date:29/04/2025
# AIM
## To write a lex program to implement lexical analyzer to recognize a few patterns.
# ALGORITHM


Start the program.

Lex program consists of three parts.

a. Declaration %%

b. Translation rules %%

c. Auxilary procedure.

The declaration section includes declaration of variables, maintest, constants and regular definitions.

Translation rule of lex program are statements of the form

a. P1 {action}

b. P2 {action}

c. Pn {action}

Write a program in the vi editor and save it with .l extension.

Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l $ cc lex.yy.c

Compile that file with C compiler and verify the output.

# INPUT
```
#include <stdio.h>
#include <ctype.h>
#include <string.h>

int isKeyword(char buffer[]) {
    char keywords[5][10] = {"if", "else", "while", "for", "int"};
    for (int i = 0; i < 5; ++i) {
        if (strcmp(buffer, keywords[i]) == 0) {
            return 1;
        }
    }
    return 0;
}

int main() {
    char ch, buffer[15];
    char operators[] = "+-*/=";
    int i = 0;

    printf("Enter your input: ");
    
    while ((ch = getchar()) != EOF) {
        if (strchr(operators, ch)) {
            printf("Operator: %c\n", ch);
        } else if (isalnum(ch)) {
            buffer[i++] = ch;
        } else if ((ch == ' ' || ch == '\n' || ch == '\t') && i != 0) {
            buffer[i] = '\0';

            if (isKeyword(buffer)) {
                printf("Keyword: %s\n", buffer);
            } else if (isdigit(buffer[0])) {
                printf("Number: %s\n", buffer);
            } else {
                printf("Identifier: %s\n", buffer);
            }
            i = 0;
        }
    }

    return 0;
}
```
# Output


![image](https://github.com/user-attachments/assets/f6ef58c8-17d3-488a-92d2-276cc3607dce)

# Result
  The lexical analyzer is implemented using lex and the output is verified.
