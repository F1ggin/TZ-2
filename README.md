# HSE_TZ2

### Бейдж статуса тестов [![Java CI](https://github.com/F1ggin/TZ-2/actions/workflows/maven.yml/badge.svg)](https://github.com/F1ggin/TZ-2/actions/workflows/maven.yml)

# NumberOperations

Это простая программа на Java, которая читает числа из файла и выполняет несколько операций над ними, таких как нахождение минимального и максимального чисел, вычисление суммы и произведения всех чисел.

## Использование

1. Убедитесь, что у вас установлена Java Development Kit (JDK).
2. Клонируйте или загрузите репозиторий.
3. Соберите проект с помощью Maven: `mvn clean install`
4. Убедитесь, что в папке с программой есть файл `numbers.txt`, содержащий числа в формате `<число_1>` `<число_2>` `...`
5. Запустите программу, используя команду `java NumberOperations`.
- Пример содержимого файла `numbers.txt`: `3 5 1 2 4`
- Ожидаемый вывод: `min: 1`, `max: 5`, `sum: 15`, `mult: 120`

## Функции программы

- Чтение чисел из файла `numbers.txt`.
- Поиск минимального числа.
- Поиск максимального числа.
- Вычисление суммы всех чисел.
- Вычисление произведения всех чисел.
- Вывод итоговых значений в стандартную консоль.

## Описание функций

- `readNumbersFromFile(String fileName)`: Считывает числа из файла с заданным именем и возвращает их в виде списка.
- `getMin(List<Integer> numbers)`: Находит и возвращает минимальное число из списка.
- `getMax(List<Integer> numbers)`: Находит и возвращает максимальное число из списка.
- `getSum(List<Integer> numbers)`: Вычисляет и возвращает сумму всех чисел в списке.
- `getMult(List<Integer> numbers)`: Вычисляет и возвращает произведение всех чисел в списке.

## Важное замечание

- Программа предполагает, что файл `numbers.txt` находится в той же директории, что и исполняемый файл программы.
- В случае возникновения ошибок при чтении файла или некорректных данных, программа выведет соответствующие сообщения об ошибке.

# NumberOperationsTest

Модуль тестирования, который проверяет корректность работы функций программы и их производительность:

## Использование

1. Подготовьте тесты в файле `src/test/java/NumberOperationsTest.java`, изменив содержимое кода.
2. Запустите тесты: `mvn test`

## Описание тестов

1. `testMin()`: Тестирует функцию `getMin()`, проверяя ее работу на различных наборах данных, включая положительные, отрицательные и смешанные числа.
2. `testMax()`: Тестирует функцию `getMax()`, проверяя ее работу на различных наборах данных, включая положительные, отрицательные и смешанные числа.
3. `testSum()`: Тестирует функцию `getSum()`, проверяя ее работу на различных наборах данных, включая положительные, отрицательные и смешанные числа.
4. `testMult()`: Тестирует функцию `getMult()`, проверяя ее работу на различных наборах данных, включая положительные, отрицательные и смешанные числа.
5. `testReadNumbersFromFile()`: Проверяет функцию чтения чисел из файла `src/test/resources/test_numbers.txt`

## Benchmark 
`Benchmark.java` - модуль для измерения времени выполнения функций программы при обработке файлов разного размера:
- Измерение времени выполнения функций `getMin()`, `getMax()`, `getSum()`, `getMult()`.
- Вывод результатов измерений в консоль.

`BenchmarkWrite.java` - аналогичный модуль, который замеряет результаты только функции `getSum()` и записывает результаты в файл.

## Результаты тестов на скорость выполнения функции `getSum()` 

- Результаты получены путем выполнения программы `BenchmarkWrite.java`, которые записываются в файл `src/main/output/results.csv`
- График построен с помощью библиотеки `matplotlib` в программе `GraphPlot.py`

| Размер входных данных | Время выполнения (в мс) |
| --------------------- |:-----------------------:|
| 5000                  | 1                       |
| 10000                 | 1                       |                  
| 100000                | 3                       |
| 500000                | 2                       |             
| 1000000               | 2                       |
| 5000000               | 4                       |
| 10000000              | 7                       |
| 50000000              | 53                      |
| 100000000             | 67                      |
| 250000000             | 163                     |
| 500000000             | 346                     |

![Figure_1](https://github.com/psycndr/TZ2/assets/102012523/cf762b84-8d27-44cd-be6c-88cc7edbe98c)

Замечаем линейную зависимость (с небольшими отклонениями) времени выполения функции от размера входных данных. 

## Рабочий процесс GitHub Actions для CI Java

- Рабочий процесс автоматизирует процесс сборки и тестирования с использованием GitHub Actions. 
- Активируется при событиях push в ветку master и может быть запущен вручную.

### Задания
- Установка Node.js 20.
- Проверка кода из репозитория.
- Установка JDK 11.
- Кэширование зависимостей Maven.
- Установка зависимостей проекта.
- Запуск тестов.
