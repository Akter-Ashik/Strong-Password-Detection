# Strong-Password-Detection


import re

def strong_password_detection(password):
    return (
        len(password) >= 12 and
        any(c.isupper() for c in password) and
        any(c.islower() for c in password) and
        any(c.isdigit() for c in password) and
        any(c in "#@$_*-" for c in password) and
        not re.search(r'(.)\1\1', password) and
        not any(word.lower() in password.lower() for word in ["password", "admin", "123456", "qwerty"]) and
        not any(info.lower() in password.lower() for info in ["john", "doe", "user123"]) and
        not re.search(r'123|abc|qwerty', password, re.IGNORECASE)
    )

# Example usage:
password = "StrongP@ss123!"
if strong_password_detection(password):
    print("The password is strong.")
else:
    print("The password is weak.")
