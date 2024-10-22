# Password-Strength-Checker

Password Strength Checker

Overview

This Java project, pass_4, is a password strength checker that evaluates the strength of a password based on several criteria such as length, presence of uppercase and lowercase letters, digits, special characters, consecutive characters, and whether the password is a palindrome. It also estimates the time required to break the password based on its complexity.

Features

The program checks the following aspects of a password:

1. Length: The password must be at least 8 characters long.


2. Uppercase Letters: At least one uppercase letter is required.


3. Lowercase Letters: At least one lowercase letter is required.


4. Digits: At least one digit is required.


5. Special Characters: At least one special character is required.


6. Consecutive Characters: The password should not have two or more consecutive identical characters.


7. Palindrome Check: The password should not be a palindrome.


8. Password Breaking Time: The program estimates the time it would take to break the password based on the number of possible combinations and a brute-force guessing rate of 10 million guesses per second.



How It Works

1. User Input: The user is prompted to enter a password (currently hardcoded as Abc in the code).


2. Strength Evaluation: The password is evaluated based on predefined criteria:

If any criterion is not met, a "Weak" message is displayed, indicating which aspect of the password is inadequate.

If all criteria are met, the password is considered "Strong."



3. Additional Checks:

Consecutive Characters: The program counts if the password contains two or more consecutive characters.

Palindrome: The program checks if the password is a palindrome.



4. Estimated Time to Break: The program calculates how long it would take to break the password through brute-force guessing, assuming 10 million guesses per second.


5. Output: The result is a detailed assessment of the password's strength and the estimated time required to break it.



Example Output

For the password Abc:

Weak: Password should have a minimum of 8 characters.
Weak: Password should have a minimum of 1 digit(s).
Weak: Password should have a minimum of 1 special character(s).
Strong: Password meets all the strength criteria.
Estimated time required to break the password: 0 days.

Code Breakdown

1. Constants:

MIN_LENGTH: Minimum length of the password.

MIN_UPPERCASE: Minimum number of uppercase letters required.

MIN_LOWERCASE: Minimum number of lowercase letters required.

MIN_DIGITS: Minimum number of digits required.

MIN_SPECIAL_CHARS: Minimum number of special characters required.

AVERAGE_PASSWORD_GUESS_PER_SECOND: Brute-force guessing speed (10 million guesses per second).



2. Main Method:

Prompts the user to enter a password.

Calls the checkPasswordStrength function to evaluate the password.



3. Password Strength Evaluation (checkPasswordStrength):

Evaluates the password's length, character composition (uppercase, lowercase, digits, special characters), consecutive characters, and whether it is a palindrome.

Returns a detailed string with the strength evaluation.



4. Helper Functions:

countConsecutiveCharacters: Counts consecutive identical characters in the password.

checkPalindrome: Checks if the password is a palindrome.

estimateTimeToBreak: Estimates the time required to break the password based on its length and character set.




Usage Instructions

1. Clone the repository.


2. Open the project in your favorite Java IDE.


3. Run the pass_4.java file.


4. Enter a password when prompted or modify the hardcoded password value to test different inputs.



Future Enhancements

Enable dynamic password input from the console.

Improve password breaking time calculation by considering common password guessing patterns (e.g., dictionary attacks).

Provide suggestions to improve password strength instead of just indicating weaknesses.


---
