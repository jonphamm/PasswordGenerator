**Secure Password Generator – Project Overview**

In today's increasingly digital and security-conscious environment, the ability to generate strong, reliable passwords is critical to protecting sensitive user data and online assets. Recognizing the widespread issue of weak or reused passwords, I developed a secure password generator designed to automate the creation of complex, random passwords that align with modern security standards.

This application accepts user input for the desired password length—enforcing a minimum of eight characters as recommended by the National Institute of Standards and Technology (NIST). The tool programmatically constructs a password that satisfies key complexity requirements: it includes at least one uppercase letter, one numerical digit, and one special character, ensuring robustness against common attack vectors such as brute-force and dictionary attacks.

By integrating user-defined parameters with security best practices, this project demonstrates my focus on usability, compliance, and practical cybersecurity principles. It reflects my capability to build tools that address real-world user behavior while upholding technical standards in software development.

**Technical Summary:**

Language: Python <br />
Libraries Used: random, string

**Key Features:**

- Enforces NIST-compliant minimum password length (8+ characters)
- Ensures inclusion of uppercase letters, digits, and special characters
- Generates randomized, secure passwords based on user-defined length
- Console-based user interaction for simplicity and accessibility

<br />
import random
import string

print("Welcome to Your Secure Password Generator!")

def generate_password(length=8):
    if length < 8:
        raise ValueError("Password must be at least 8 characters long.")

    # Ensure at least one of each required character type
    upper = random.choice(string.ascii_uppercase)
    digit = random.choice(string.digits)
    symbol = random.choice(string.punctuation)

    # Fill the rest of the password
    remaining_length = length - 3
    all_chars = string.ascii_letters + string.digits + string.punctuation
    remaining_chars = [random.choice(all_chars) for _ in range(remaining_length)]

    # Combine and shuffle
    password_list = list(upper + digit + symbol + ''.join(remaining_chars))
    random.shuffle(password_list)

    return ''.join(password_list)

# Loop to allow multiple password generations
while True:
    try:
        length = int(input("Enter password length (minimum 8): "))
        if length < 8:
            print("Password must be at least 8 characters long.")
            continue
        print("Generated Password:", generate_password(length))
    except ValueError:
        print("Please enter a valid number.")
        continue

    again = input("Would you like to generate another password? (yes/no): ").strip().lower()
    if again != 'yes':
        print("Goodbye! Have a great day!")
        break
