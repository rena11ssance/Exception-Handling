# Обработка исключений

Задача. Смоделируйте работу простого калькулятора. Программа должна запрашивать 2 числа, а затем – код операции (например, 1 – сложение, 2 – вычитание, 3 – произведение, 4 – частное). После этого на консоль выводится ответ. Используйте обработку исключений для защиты от ввода некорректных данных.

Решение: 
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Task_1
{
    internal class Program
    {
        static void Main(string[] args)
        {
                Console.WriteLine("Вас приветствует калькулятор!");

                int x = 0;
                int y = 0;

                try
                {
                    Console.Write("Введите целое число. X = ");
                    x = Convert.ToInt32(Console.ReadLine());

                    Console.Write("Введите целое число. Y = ");
                    y = Convert.ToInt32(Console.ReadLine());
                }

                catch (FormatException)
                {
                    Console.Write("Ошибка! Входная строка имела неверный формат.");
                    return;
                }

                catch (Exception ex)
                {
                    Console.Write("Неожиданная ошибка: " + ex.Message);
                    return;
                }

                Console.WriteLine("Введите код операции: ");
                Console.WriteLine($"\t1 - сложение;");
                Console.WriteLine($"\t2 - вычитание;");
                Console.WriteLine($"\t3 - произведение;");
                Console.WriteLine($"\t4 - частное.");

                Console.Write("Ваш выбор: ");
                int userChoice = Convert.ToInt32(Console.ReadLine());
                double result = 0;

                try
                {
                    switch (userChoice)
                    {
                        case 1:
                            result = x + y;
                            break;

                        case 2:
                            result = x - y;
                            break;

                        case 3:
                            result = x * y;
                            break;

                        case 4:
                            result = (double)x / y;
                            break;

                        default:
                            Console.WriteLine("Нет операции с указанным номером.");
                            return;
                    }
                }

                catch (OverflowException)
                {
                    Console.Write("Ошибка: число слишком большое или слишком маленькое");
                    return;
                }

                catch (DivideByZeroException)
                {
                    Console.Write("Ошибка: деление на ноль.");
                    return;
                }

                catch (Exception ex)
                {
                    Console.Write("Неожиданная ошибка: " + ex.Message);
                    return;
                }

                Console.Write("Ваш результат: {0}.", result);

        }
    }
}


```
