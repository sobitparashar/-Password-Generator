import random
import string

def generate_password(length=12):
    if length < 4:
        return " Password too short! Choose at least 4 characters."

    lowercase = string.ascii_lowercase
    uppercase = string.ascii_uppercase
    digits = string.digits
    symbols = string.punctuation

    # Ensure at least one character of each type
    password = [
        random.choice(lowercase),
        random.choice(uppercase),
        random.choice(digits),
        random.choice(symbols)
    ]

    # Fill the rest of the password length
    all_chars = lowercase + uppercase + digits + symbols
    password += random.choices(all_chars, k=length - 4)
    random.shuffle(password)

    return ''.join(password)

def main():
    print("Welcome to the Password Generator!")

    while True:
        try:
            length = int(input("\nEnter desired password length (min 4): "))
            password = generate_password(length)
            print("Generated password:", password)
        except ValueError:
            print(" Please enter a valid number.")

        again = input("Do you want to generate another password? (yes/no): ").lower()
        if again != "yes":
            print("Goodbye! Stay secure ")
            break

if _name_ == "_main_":
    main()
