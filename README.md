# Password-Strength-Checker

This Java project assesses password strength by analysing factors like length, character diversity, and vulnerability to common hacking methods. It
categorizes passwords as weak, medium, or strong and estimates the time needed for potential cracking attempts. Built in IntelliJ IDEA, it demonstrates
Java programming skills and knowledge of cybersecurity principles.

import java.util.Scanner;

public class pass_4 {
    private static final int MIN_LENGTH = 8;
    private static final int MIN_UPPERCASE = 1;
    private static final int MIN_LOWERCASE = 1;
    private static final int MIN_DIGITS = 1;
    private static final int MIN_SPECIAL_CHARS = 1;
    private static final int AVERAGE_PASSWORD_GUESS_PER_SECOND = 10_000_000;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a password: ");
        String password = "Abc";
        String result = checkPasswordStrength(password);
        System.out.println(result);
    }

    public static String checkPasswordStrength(String password) {
        StringBuilder strength = new StringBuilder();

        if (password.length() < MIN_LENGTH) {
            strength.append("Weak: Password should have a minimum of ")
                    .append(MIN_LENGTH)
                    .append(" characters.\n");
        }

        int uppercaseCount = 0;
        int lowercaseCount = 0;
        int digitCount = 0;
        int specialCharCount = 0;
        for (char c : password.toCharArray()) {
            if (Character.isUpperCase(c)) {
                uppercaseCount++;
            } else if (Character.isLowerCase(c)) {
                lowercaseCount++;
            } else if (Character.isDigit(c)) {
                digitCount++;
            } else {
                specialCharCount++;
            }
        }

        if (uppercaseCount < MIN_UPPERCASE) {
            strength.append("Weak: Password should have a minimum of ")
                    .append(MIN_UPPERCASE)
                    .append(" uppercase letter(s).\n");
        }

        if (lowercaseCount < MIN_LOWERCASE) {
            strength.append("Weak: Password should have a minimum of ")
                    .append(MIN_LOWERCASE)
                    .append(" lowercase letter(s).\n");
        }

        if (digitCount < MIN_DIGITS) {
            strength.append("Weak: Password should have a minimum of ")
                    .append(MIN_DIGITS)
                    .append(" digit(s).\n");
        }

        if (specialCharCount < MIN_SPECIAL_CHARS) {
            strength.append("Weak: Password should have a minimum of ")
                    .append(MIN_SPECIAL_CHARS)
                    .append(" special character(s).\n");
        }

        if (strength.length() == 0) {
            strength.append("Strong: Password meets all the strength criteria.\n");
        }

        int consecutiveCharCount = countConsecutiveCharacters(password);
        if (consecutiveCharCount > 0) {
            strength.append("Weak: Password contains ")
                    .append(consecutiveCharCount)
                    .append(" or more consecutive characters.\n");
        }

        boolean isPalindrome = checkPalindrome(password);
        if (isPalindrome) {
            strength.append("Weak: Password is a palindrome.\n");
        }

        String estimatedTimeToBreak = estimateTimeToBreak(password);
        strength.append("Estimated time required to break the password: ")
                .append(estimatedTimeToBreak)
                .append(".\n");

        return strength.toString();
    }

    private static int countConsecutiveCharacters(String password) {
        int maxConsecutive = 2;
        int count = 1;
        for (int i = 1; i < password.length(); i++) {
            if (password.charAt(i) == password.charAt(i - 1)) {
                count++;
            } else {
                count = 1;
            }
            if (count >= maxConsecutive) {
                return count;
            }
        }
        return 0;
    }

    private static boolean checkPalindrome(String password) {
        int n = password.length();
        for (int i = 0; i < n / 2; i++) {
            if (password.charAt(i) != password.charAt(n - i - 1)) {
                return false;
            }
        }
        return true;
    }

    private static String estimateTimeToBreak(String password) {
        long possibleCombinations = (long) Math.pow(94, password.length());
        long secondsToBreak = possibleCombinations / AVERAGE_PASSWORD_GUESS_PER_SECOND;
        long daysToBreak = secondsToBreak / (24 * 3600);
        return daysToBreak + " days";
    }
}
