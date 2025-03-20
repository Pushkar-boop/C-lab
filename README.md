Write a program to perform the following operators on Strings without using String functions 

a. To find the Length of String. 

b. To concatenate two string. 

c. To find Reverse of a string. 

d. To copy one string to another string.

#include <stdio.h>

// Function to calculate length of string
int findLength(char str[]) {
    int i = 0;
    while (str[i] != '\0') {
        i++;
    }
    return i;
}

// Function to concatenate two strings
void concatenate(char str1[], char str2[], char result[]) {
    int i = 0, j = 0;
    
    // Copy first string to result
    while (str1[i] != '\0') {
        result[i] = str1[i];
        i++;
    }
    
    // Copy second string to result
    while (str2[j] != '\0') {
        result[i] = str2[j];
        i++;
        j++;
    }
    result[i] = '\0'; // Add null character at the end
}

// Function to reverse a string
void reverseString(char str[], char rev[]) {
    int len = findLength(str);
    int i;
    
    for (i = 0; i < len; i++) {
        rev[i] = str[len - i - 1];
    }
    rev[len] = '\0'; // Add null character
}

// Function to copy one string to another
void copyString(char source[], char destination[]) {
    int i = 0;
    while (source[i] != '\0') {
        destination[i] = source[i];
        i++;
    }
    destination[i] = '\0'; // Add null character
}

int main() {
    char str1[100], str2[100], result[200], rev[100], copy[100];
    int length;

    // Input for first string
    printf("Enter first string: ");
    scanf("%s", str1);
    
    // Input for second string
    printf("Enter second string: ");
    scanf("%s", str2);

    // Finding length of first string
    length = findLength(str1);
    printf("\nLength of first string: %d", length);

    // Concatenating strings
    concatenate(str1, str2, result);
    printf("\nConcatenated string: %s", result);

    // Reversing first string
    reverseString(str1, rev);
    printf("\nReversed string: %s", rev);

    // Copying first string to another
    copyString(str1, copy);
    printf("\nCopied string: %s\n", copy);

    return 0;
}


Output 

Enter first string: hello
Enter second string: world

Length of first string: 5
Concatenated string: helloworld
Reversed string: olleh
Copied string: hello
