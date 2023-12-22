using System;
class HelloWorld {
  static void Main() {
    Console.WriteLine("Hello World");
  }
}
from string import (
    punctuation, whitespace, digits,
    ascii_lowercase, ascii_uppercase)


def is_valid_password(password):
    new_password = password.strip()

    MIN_SIZE = 6
    MAX_SIZE = 20
    password_size = len(new_password)

    if password_size < MIN_SIZE or password_size > MAX_SIZE:
        return False

    valid_chars = {'-', '_', '.', '!', '@', '#', '$', '^', '&', '(', ')'}
    invalid_chars = set(punctuation + whitespace) - valid_chars

    for char in invalid_chars:
        if char in new_password:
            return False

    password_has_digit = False

    for char in password:
        if char in digits:
            password_has_digit = True
            break

    if not password_has_digit:
        return False

    password_has_lowercase = False

    for char in password:
        if char in ascii_lowercase:
            password_has_lowercase = True
            break

    if not password_has_lowercase:
        return False


    password_has_uppercase = False

    for char in password:
        if char in ascii_uppercase:
            password_has_uppercase = True
            break

    if not password_has_uppercase:
        return False

    return True
