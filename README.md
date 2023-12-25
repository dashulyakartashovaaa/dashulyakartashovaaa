using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Введите пароль для проверки:");
        string password = Console.ReadLine();

        bool isStrong = CheckPasswordStrength(password);

        if (isStrong)
        {
            Console.WriteLine("Пароль сильный.");
        }
        else
        {
            Console.WriteLine("Пароль слабый.");
        }
    }

    static bool CheckPasswordStrength(string password)
    {
        // Проверка длины пароля
        if (password.Length < 8)
        {
            return false;
        }

        // Проверка наличия спецсимволов
        if (!ContainsSpecialCharacter(password))
        {
            return false;
        }

        // Проверка наличия цифр
        if (!ContainsDigit(password))
        {
            return false;
        }

        // Проверка наличия символов в верхнем и нижнем регистрах
        if (!ContainsLowerAndUpperCase(password))
        {
            return false;
        }

        return true;
    }

    static bool ContainsSpecialCharacter(string password)
    {
        foreach (char c in password)
        {
            if (!char.IsLetterOrDigit(c))
            {
                return true;
            }
        }
        return false;
    }

    static bool ContainsDigit(string password)
    {
        foreach (char c in password)
        {
            if (char.IsDigit(c))
            {
                return true;
            }
        }
        return false;
    }

    static bool ContainsLowerAndUpperCase(string password)
    {
        bool hasLower = false;
        bool hasUpper = false;

        foreach (char c in password)
        {
            if (char.IsLower(c))
            {
                hasLower = true;
            }
            else if (char.IsUpper(c))
            {
                hasUpper = true;
            }
        }

        return hasLower && hasUpper;
    }
}

