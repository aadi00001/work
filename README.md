%{
#include <stdio.h>

int charCount = 0, wordCount = 0, spaceCount = 0, lineCount = 0;
FILE *outFile; // output file pointer
%}

%%

[a-zA-Z0-9_]+   { wordCount++; charCount += yyleng; }
[ \t]           { spaceCount++; charCount++; }
\n              { lineCount++; charCount++; }
.               { charCount++; }

%%

int main() {
    FILE *fp = fopen("Input.txt", "r");
    if (!fp) {
        printf("Error opening Input.txt\n");
        return 1;
    }

    outFile = fopen("output.txt", "w");
    if (!outFile) {
        printf("Error creating output.txt\n");
        return 1;
    }

    yyin = fp;
    yylex();
    fclose(fp);

    fprintf(outFile, "Total Characters: %d\n", charCount);
    fprintf(outFile, "Total Words: %d\n", wordCount);
    fprintf(outFile, "Total White Spaces: %d\n", spaceCount);
    fprintf(outFile, "Total Lines: %d\n", lineCount);

    fclose(outFile);
    return 0;
}

int yywrap() {
    return 1;
}





