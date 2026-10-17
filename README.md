# c-programming-quiz-app
A beginner-friendly C quiz application featuring 20 multiple-choice questions, automatic scoring, answer feedback, and performance evaluation.


include <stdio.h>

#define TOTAL_QUESTIONS 20

int main(void) {
    int answers[TOTAL_QUESTIONS] = {0};
    int score = 0;

    const char *questions[TOTAL_QUESTIONS] = {
        "Which function starts a C program?",
        "Which header file supports printf() and scanf()?",
        "Which symbol ends most C statements?",
        "Which format specifier prints an int?",
        "Which data type stores a character?",
        "Which operator checks equality?",
        "Which loop checks its condition before each iteration?",
        "Which statement exits the nearest loop?",
        "Which keyword makes a decision?",
        "What is the result of 10 % 3?",
        "Which operator means logical AND?",
        "Which loop runs its body at least once?",
        "Which keyword declares a read-only object?",
        "Which function reads formatted input?",
        "What is the first index of a C array?",
        "Which operator obtains a variable's address?",
        "Which keyword returns from a function?",
        "Which type represents floating-point values?",
        "Which statement selects among cases?",
        "Which operator increments a variable by one?"
    };

    const char *options[TOTAL_QUESTIONS][4] = {
        {"start()", "main()", "run()", "begin()"},
        {"stdlib.h", "string.h", "stdio.h", "math.h"},
        {":", ";", ",", "."},
        {"%f", "%c", "%d", "%s"},
        {"char", "int", "float", "double"},
        {"=", "==", "!=", "<="},
        {"do-while", "while", "switch", "if"},
        {"skip", "continue", "break", "return"},
        {"if", "include", "define", "printf"},
        {"3", "1", "0", "3.33"},
        {"&&", "||", "!", "&"},
        {"for", "while", "do-while", "switch"},
        {"fixed", "const", "static", "auto"},
        {"printf()", "puts()", "scanf()", "strlen()"},
        {"1", "-1", "0", "Depends on the array"},
        {"*", "&", "%", "#"},
        {"break", "continue", "return", "case"},
        {"int", "char", "float", "void"},
        {"switch", "while", "typedef", "goto"},
        {"--", "+=", "++", "**"}
    };

    /* Correct options use numbers 1 to 4. */
    int correct[TOTAL_QUESTIONS] = {
        2, 3, 2, 3, 1,
        2, 2, 3, 1, 2,
        1, 3, 2, 3, 3,
        2, 3, 3, 1, 3
    };

    printf("====================================\n");
    printf("       C PROGRAMMING QUIZ APP\n");
    printf("====================================\n");
    printf("Instructions: Enter option 1, 2, 3 or 4.\n");
    printf("Each correct answer earns 1 mark.\n");

    for (int i = 0; i < TOTAL_QUESTIONS; i++) {
        printf("\n------------------------------------\n");
        printf("Question %d/%d\n", i + 1, TOTAL_QUESTIONS);
        printf("%s\n", questions[i]);

        for (int j = 0; j < 4; j++) {
            printf("%d. %s\n", j + 1, options[i][j]);
        }

        printf("Your answer (1-4): ");

        if (scanf("%d", &answers[i]) != 1) {
            printf("\nInvalid input. Please run the quiz again.\n");
            return 1;
        }

        while (answers[i] < 1 || answers[i] > 4) {
            printf("Please enter a number from 1 to 4: ");

            if (scanf("%d", &answers[i]) != 1) {
                printf("\nInvalid input. Please run the quiz again.\n");
                return 1;
            }
        }

        if (answers[i] == correct[i]) {
            printf("Correct answer! +1 mark\n");
            score++;
        } else {
            printf("Wrong answer.\n");
            printf("Correct answer: %s\n",
                   options[i][correct[i] - 1]);
        }
    }

    printf("\n====================================\n");
    printf("             QUIZ RESULT\n");
    printf("====================================\n");
    printf("Total questions : %d\n", TOTAL_QUESTIONS);
    printf("Correct answers : %d\n", score);
    printf("Wrong answers   : %d\n", TOTAL_QUESTIONS - score);
    printf("Final score     : %d/%d\n", score, TOTAL_QUESTIONS);
    printf("Percentage      : %.2f%%\n",
           (score * 100.0) / TOTAL_QUESTIONS);

    if (score >= 18) {
        printf("Performance: Excellent!\n");
    } else if (score >= 14) {
        printf("Performance: Very good!\n");
    } else if (score >= 10) {
        printf("Performance: Good effort!\n");
    } else {
        printf("Performance: Keep practising!\n");
    }

    printf("\nThank you for using my C Quiz App!\n");
    printf("====================================\n");

    return 0;
}
    