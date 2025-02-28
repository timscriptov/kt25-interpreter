# kt25-interpreter

# Документация

## Основные концепции

* **Классы:** Организация кода в классы.
* **Функции:** Определение функций внутри классов и вне их.
* **Переменные:** Объявление переменных с типами данных.
* **Списки:** Поддержка списков различных типов.
* **Циклы:** Использование циклов `for`, `while`, `do-while` и `repeat` для итерации по спискам и диапазонам.
* **Комментарии:** Поддержка однострочных комментариев (`//`).
* **Операторы:** Поддержка арифметических, логических и операторов сравнения, а также инкремента и декремента.
* **Присваивание:** Оператор присваивания `=` и оператор `+=`.
* **Типы данных:** `Char`, `Int`, `String`, `Bool`, `Array<T>`, `Unit`.
* **Вывод на консоль:** Использование функции `print`.
* **Необязательная точка с запятой:** Символ `;` не обязателен в конце строки.
* **Условные операторы:** `if-else`
* **Функции без тела:** Объявление функций без тела.
* **Интервалы:** Представление диапазонов значений.
* **Статические вызовы функций:** Вызов функций из других классов без создания экземпляра.
* **Обратные интервалы:** Использование `downTo` для создания обратных интервалов.
* **Исключающие интервалы:** Использование `until` для создания интервалов, исключающих последний элемент.
* **Тернарный оператор `if`:** Использование `if` как выражения.
* **Унарный минус:** Поддержка унарного минуса для целых чисел.
* **Интерполяция строк:** Вставка переменных и выражений в строки.
* **Операторы `break` и `continue`:** Управление выполнением циклов.
* **Операторы `in` и `!in`:** Проверка наличия или отсутствия элемента в коллекции.

## Структура программы

Программа состоит из классов, каждый из которых может содержать поля (переменные) и методы (функции). Точкой входа в программу является функция `main` класса `Main`.

```kt
class Main {
    fun main(args: Array<String>) {
        // Код программы
    }
}
```

## Объявление переменных

Переменные объявляются с использованием ключевых слов `val` (для констант) и `var` (для переменных, которые могут быть изменены).

```kt
val x: Int = 10;
var y: String = "Hello";
```

## Типы данных

* **Char:** Символ.
* **Int:** Целые числа.
* **String:** Строки.
* **Bool:** Логические значения (`true`, `false`).
* **Array<T>:** Списки элементов типа `T`.
* **Unit:** Используется для функций, которые не возвращают значение. Указывать тип Unit не обязательно.

## Интерполяция строк

Интерполяция строк позволяет вставлять значения переменных и выражения внутрь строк.

```kt
val x: Int = 1;
val y: Int = 2;
val s: String = "X: $x Y: $y Sum: ${x + y}";
println(s); // Выводит "X: 1 Y: 2 Sum: 3"

val name: String = "Alice";
println("Hello, $name!"); // Выводит "Hello, Alice!"
```

## Списки

Списки создаются с помощью функции `arrayOf`.

```kt
val numbers: Array<Int> = arrayOf(1, 2, 3);
val strings: Array<String> = arrayOf("a", "b", "c");
```

## Циклы

Цикл for используется для итерации по элементам списка или диапазону.

```kt
val numbers: Array<Int> = arrayOf(1, 2, 3);
for (number in numbers) {
    print(number);
}

for (i in 1..5) {
    print(i); // Выводит 1, 2, 3, 4, 5
}

for (i in 10 downTo 1) {
    print(i); // Выводит 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
}

for (i in 1..8 step 2) {
    print(i); // Выводит 1, 3, 5, 7
}

for (i in 8 downTo 1 step 2) {
    print(i); // Выводит 8, 6, 4, 2
}

for (i in 1 until 10) {
    print(i); // Выводит 1, 2, 3, 4, 5, 6, 7, 8, 9
}
```

## Цикл while

Цикл `while` выполняет блок кода до тех пор, пока условие истинно. Условие проверяется перед каждой итерацией цикла.

```kt
var i: Int = 0;
while (i < 5) {
    print("while: " + i);
    i += 1;
}
```

В этом примере цикл будет выполняться, пока значение `i` меньше 5.

## Цикл do-while

Цикл `do-while` выполняет блок кода хотя бы один раз, а затем повторяет выполнение, пока условие истинно. Условие проверяется после каждой итерации цикла.

```kt
var j: Int = 0;
do {
    print("do-while: " + j);
    j += 1;
} while (j < 5);
```

В этом примере цикл выполнится как минимум один раз и будет продолжаться, пока значение `j` меньше 5.

## Цикл repeat

Цикл `repeat` выполняет блок кода заданное количество раз.

```kt
repeat(5) {
    println("Hello");
}
```

В этом примере цикл выведет "Hello" 5 раз.

## Функции

Функции объявляются с помощью ключевого слова `fun`.

```kt
fun greet(name: String): String {
    return "Hello, " + name;
}
```

## Вызов функций

Функции вызываются по имени с передачей аргументов.

```kt
val message: String = greet("World");
print(message);
```

## Вызов функций из Main

```kt
class Main {
    fun main(args: Array<String>) {
        printMessage("Hello from Main");
        val result: Int = add(5, 3);
        print("Result: " + result);
    }

    fun printMessage(message: String) {
        print(message);
    }

    fun add(a: Int, b: Int): Int {
        return a + b;
    }
}
```

## Статический вызов функций из другого класса

```kt
class Helper {
    fun multiply(a: Int, b: Int): Int {
        return a * b;
    }
}

class Main {
    fun main(args: Array<String>) {
        val result: Int = Helper.multiply(4, 6);
        print("Multiplication result: " + result);
    }
}
```

## Функции без тела

Функции без тела могут быть объявлены с использованием оператора `=`. Такие функции могут содержать только одно выражение.

```kt
fun square(x: Int): Int = x * x;

fun printMessage(message: String) = print(message);

fun printSum(a: Int, b: Int): Unit = print("Sum: " + (a + b));
```

## Операторы

* **Арифметические:** `+`, `-`, `*`, `/`, `%`.
* **Сравнения:** `<`, `>`, `<=`, `>=`, `==`, `!=`.
* **Логические:** `+=`.
* **Унарный минус:** `-`
* **Инкремент:** `++`
* **Декремент:** `--`

## Операторы инкремента и декремента

Язык поддерживает операторы инкремента `++` и декремента `--` для увеличения и уменьшения значений переменных на единицу.

### Оператор инкремента `++`

Оператор `++` увеличивает значение переменной на 1. Он может использоваться как префиксный (`++x`) или постфиксный (`x++`) оператор.

* **Постфиксный инкремент (`x++`):** Возвращает текущее значение переменной, а затем увеличивает его на 1.
* **Префиксный инкремент (`++x`):** Увеличивает значение переменной на 1, а затем возвращает новое значение.

```kt
var x: Int = 5;
val y: Int = x++; // y = 5, x = 6
val z: Int = ++x; // z = 7, x = 7
```

### Оператор декремента `--`

Оператор `--` уменьшает значение переменной на 1. Он может использоваться как префиксный (`--x`) или постфиксный (`x--`) оператор.

* **Постфиксный декремент (`x--`):** Возвращает текущее значение переменной, а затем уменьшает его на 1.
* **Префиксный декремент (`--x`):** Уменьшает значение переменной на 1, а затем возвращает новое значение.

```kt
var x: Int = 5;
val y: Int = x--; // y = 5, x = 4
val z: Int = --x; // z = 3, x = 3
```

### Использование в циклах

Операторы `++` и `--` часто используются в циклах для изменения значений

```kt
var j: Int = 5;
while (j > 0) {
    print("j: " + j--); // Выводит j: 5, j: 4, j: 3, j: 2, j: 1
}
```

## Условные операторы

Условные операторы `if-else` позволяют выполнять код в зависимости от условий.

```kt
val x: Int = 10;
if (x + 2 > 5) {
    print("x больше 5");
} else {
    print("x не больше 5");
}
```

## Тернарный оператор if

Тернарный оператор `if` позволяет использовать `if` как выражение.

```kt
val x: Int = 10;
val b: Int = if (x > 5) { x * 2 } else { -1 };
print("b: " + b); // Выводит 20
```

## Операторы `in` и `!in`


**Оператор `in`**

Оператор `in` используется для проверки, содержит ли коллекция (список или диапазон) определенный элемент.

**Синтаксис:**

```kt
element in collection
```

* `element`: Выражение, значение которого нужно проверить на наличие в коллекции.
* `collection`: Выражение, представляющее собой коллекцию (список или диапазон).

**Примеры:**

```kt
val numbers = arrayOf(1, 2, 3, 4, 5)
val result1 = 3 in numbers // true
val result2 = 6 in numbers // false

val range = 1..10
val result3 = 7 in range // true
val result4 = 15 in range // false
```

**Оператор `!in`**

Оператор `!in` является противоположностью оператора `in`. Он используется для проверки, что коллекция не содержит определенный элемент.

**Синтаксис:**

```kt
element !in collection
```

* `element`: Выражение, значение которого нужно проверить на отсутствие в коллекции.
* `collection`: Выражение, представляющее собой коллекцию (список или диапазон).

```kt
val numbers = arrayOf(1, 2, 3, 4, 5)
val result1 = 3 !in numbers // false
val result2 = 6 !in numbers // true

val range = 1..10
val result3 = 7 !in range // false
val result4 = 15 !in range // true
```

**Использование в условных выражениях:**

Операторы `in` и `!in` часто используются в условных выражениях:

```kt
val x: Int = 5
if (x in 1..10) {
    println("x находится в диапазоне от 1 до 10")
}

val name: String = "Alice"
val array: List<String> = arrayOf("Bob", "Charlie")
if (name !in array) {
    println("Имя не Боб и не Чарли")
}
```

## Комментарии

Однострочные комментарии начинаются с `//`.

```kt
// Это комментарий
val x: Int = 10;
```

## Пример программы

```kt
class Main {
    fun main(args: Array<String>) {
        testFibonacci();
        testCounter();
        testStringConcatenation();
        testArrayIteration();
        testRangeForLoops();
        testIfElse();
        testFunctionCalls();
        testIfExpression();
        testWhileLoop();
        testDoWhileLoop();
        testStringInterpolation();
        testIncrementDecrement();
        testBreakContinue();
        testRepeatLoop();
        testCharLiterals();
        testInNotIn();
    }

    fun testFibonacci() {
        val n: Int = 10; // Вычислить 10-е число Фибоначчи
        val result: Int = fibonacci(n);
        println("Fibonacci(" + n + "): " + result); // Выводит Fibonacci(10): 55
    }

    fun testCounter() {
        var counter: Int = 1;
        counter += 1;
        println("Counter: " + counter); // out: 3
    }

    fun testStringConcatenation() {
        var text: String = "Hello";
        text += ", world!";
        println("Text: " + text);
    }

    fun testArrayIteration() {
        val numbers: Array<Int> = arrayOf(1, 2, 3);
        for (number in numbers) {
            println(number);
        }
    }

    fun testRangeForLoops() {
        val x: Int = 10;
        println("for(i in 3..x):")
        for (i in 3..x) {
            println(i);
        }
        println("for(i in 3..x step-2):")
        for (i in 3..x step 2) {
            println(i);
        }
        println("for(i in x downTo 3):")
        for (i in x downTo 3) {
            println(i);
        }
        println("for(i in x downTo 3 step-2):")
        for (i in x downTo 3 step 2) {
            println(i);
        }
        println("for(i in 1 until x):")
        for (i in 1 until x) {
            println(i);
        }
    }

    fun testIfElse() {
        val x: Int = 10;
        if (x + 2 > 5) {
            println("x больше 5");
        } else {
            println("x не больше 5");
        }
    }

    fun testFunctionCalls() {
        printMessage("Hello from Main");
        val result: Int = add(5, 3);
        println("Result: " + result);
        val multResult: Int  = Helper.multiply(4, 6);
        println("Multiplication result: " + multResult);
    }

    fun testIfExpression() {
        val x: Int = 10;
        val b: Int = if (x > 5) {
            x * 2
        } else { -1 };
        println("b: " + b);
    }

    fun testWhileLoop() {
        var i: Int = 0;
        while (i < 5) {
            println("while: " + i);
            i += 1;
        }
    }

    fun testDoWhileLoop() {
        var j: Int = 0;
        do {
            println("do-while: " + j);
            j += 1;
        } while (j < 5);
        var k: Int = 0;
        while (++k < 5) {
            println("++k: " + k);
        }
    }

    fun testStringInterpolation() {
        val a: Int = 10;
        val b: Int = 20;
        println("a = $a, b = $b, sum = ${a + b}");
        val name: String = "Alice";
        println("Hello, $name!");
    }

    fun testIncrementDecrement() {
        var incrementVar: Int = 5;
        val postfixIncrement: Int = incrementVar++;
        println("Постфиксный инкремент: incrementVar = " + incrementVar + ", postfixIncrement = " + postfixIncrement); // Выводим результаты
        incrementVar = 5;
        val prefixIncrement: Int = ++incrementVar;
        println("Префиксный инкремент: incrementVar = " + incrementVar + ", prefixIncrement = " + prefixIncrement); // Выводим результаты
        var decrementVar: Int = 5;
        val postfixDecrement: Int = decrementVar--;
        println("Постфиксный декремент: decrementVar = " + decrementVar + ", postfixDecrement = " + postfixDecrement); // Выводим результаты
        decrementVar = 5;
        val prefixDecrement: Int = --decrementVar;
        println("Префиксный декремент: decrementVar = " + decrementVar + ", prefixDecrement = " + prefixDecrement); // Выводим результаты
    }

    fun testBreakContinue() {
        println("Пример for(i in 1..10) break и continue:");
        for (i in 1..10) {
            if (i == 5) {
                println("continue at i = 5");
                continue
            }
            if (i == 8) {
                println("break at i = 8");
                break
            }
            println(i);
        }
        var i4: Int = 1;
        println("Пример while() break и continue:");
        while (i4 < 10) {
            if (i4 == 5) {
                i4 = i4 + 1
                println("continue at i = 5");
                continue
            }
            if (i4 == 8) {
                println("break at i = 8");
                break
            }
            println(i4);
            i4 = i4 + 1;
        }
    }

    fun testRepeatLoop() {
        val r1: Int = 0
        repeat(5) {
            println("Repeat ${r1++}")
        }
    }

    fun testCharLiterals() {
        val myChar: Char = 'A';
        println(myChar); // Выводит A
        println('B'); // Выводит B
    }

    fun testInNotIn() {
        val x: Bool = 1 in 0..9;
        println("1 in 0..9: " + x);
        val y: Bool = 10 in 0..9;
        println("10 in 0..9: " + y);
        val list: Array<Int> = arrayOf(0, 3, 6, 7, 9);
        val z: Bool = 3 !in list;
        println("3 !in list: " + z);
        val w: Bool = 5 !in list;
        println("5 !in list: " + w);
        val v: Bool = 3 in list;
        println("3 in list: " + v);
    }

    fun printMessage(message: String) {
        println(message);
    }

    fun add(a: Int, b: Int): Int {
        return a + b;
    }
    fun fibonacci(n: Int): Int {
        if (n <= 1) {
            return n;
        }
        var a: Int = 0;
        var b: Int = 1;
        for (i in 2..n) {
            val temp: Int = a + b;
            a = b;
            b = temp;
        }
        return b;
    }
}

class Helper {
    fun multiply(a: Int, b: Int): Int {
        return a * b;
    }
}
```
