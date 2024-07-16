@ -0,0 +1,53 @@
import re

def assess_password_strength(password):
    strength = 0
    feedback = []

    # Check length
    if len(password) >= 8:
        strength += 1
    else:
        feedback.append("Password should be at least 8 characters long.")

    # Check for uppercase letters
    if re.search(r'[A-Z]', password):
        strength += 1
    else:
        feedback.append("Password should include at least one uppercase letter.")

    # Check for lowercase letters
    if re.search(r'[a-z]', password):
        strength += 1
    else:
        feedback.append("Password should include at least one lowercase letter.")

    # Check for numbers
    if re.search(r'[0-9]', password):
        strength += 1
    else:
        feedback.append("Password should include at least one number.")

    # Check for special characters
    if re.search(r'[!@#$%^&*(),.?":{}|<>]', password):
        strength += 1
    else:
        feedback.append("Password should include at least one special character.")

    # Determine strength level
    if strength == 5:
        feedback.insert(0, "Password is very strong.")
    elif strength == 4:
        feedback.insert(0, "Password is strong.")
    elif strength == 3:
        feedback.insert(0, "Password is moderate.")
    else:
        feedback.insert(0, "Password is weak.")

    return feedback

# Example usage
password = input("Enter a password to assess: ")
feedback = assess_password_strength(password)
for comment in feedback:
    print(comment)
