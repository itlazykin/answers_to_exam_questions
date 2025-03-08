## IO

[1. Что такое поток ввода-вывода?](#1-Что-такое-поток-ввода-вывода)

[2. Что такое Java IO?](#2-Что-такое-Java-IO)

[3. Что такое Java NIO?](#3-Что-такое-Java-NIO)

[4. Что такое NIO 2?](#4-Что-такое-NIO-2)

[5. Что такое Scanner? ](#5-Что-такое-Scanner)

[6. Как работает Scanner внутри?](#6-Как-работает-Scanner-внутри)

[7. Какие базовые методы существуют в Scanner?](#7-Какие-базовые-методы-существуют-в-Scanner)

[8. Что такое байтовый поток? Как он реализован внутри?](#8-Что-такое-байтовый-поток-Как-он-реализован-внутри)

[9. Что такое символьный поток. Как он реализован внутри?](#9-Что-такое-символьный-поток-Как-он-реализован-внутри)

[10. Что такое буферизированный поток? ](#10-Что-такое-буферизированный-поток)

[11. Какие классы-обёртки позволяют ускорить чтение или запись за счет использования буфера?](#11-Какие-классы-обёртки-позволяют-ускорить-чтение-или-запись-за-счет-использования-буфера)

[12. Как осуществляется ввод и вывод из командной строки?](#12-Как-осуществляется-ввод-и-вывод-из-командной-строки)

[13. Что такое класс Console? Расскажите его АПИ.](#13-Что-такое-класс-Console-Расскажите-его-АПИ)

[14. Что такое поток данных? Data stream.](#14-Что-такое-поток-данных-Data-stream)

[15. Что такое поток объектов, Object stream.](#15-Что-такое-поток-объектов-Object-stream)

[16. Что такое Path? Как он реализуется на разных ОС?](#16-Что-такое-Path-Как-он-реализуется-на-разных-ОС)

[17. Как получить список файлов?](#17-Как-получить-список-файлов)

[18. Как проверить что файловая сущность является файлом или папкой?](#18-Как-проверить-что-файловая-сущность-является-файлом-или-папкой)

[19. Как удалить файл?](#19-Как-удалить-файл)

[20. Как переместить файл?](#20-Как-переместить-файл)

[21. Как управлять атрибутами файла?](#21-Как-управлять-атрибутами-файла)

[22. Как создать файл?](#22-Как-создать-файл)

[23. Как создать директорию?](#23-Как-создать-директорию)

[24. Как записать в файл?](#24-Как-записать-в-файл)

[25. Как прочитать данные из файла?](#25-Как-прочитать-данные-из-файла)

[26. Для чего нужны классы PrintStream и PrintWriter? В чем их различие?](#26-Для-чего-нужны-классы-PrintStream-и-PrintWriter-В-чем-их-различие)

[27. Что такое потоки байтовых массивов? Как они устроены?](#27-Что-такое-потоки-байтовых-массивов-Как-они-устроены)

[28. Зачем нужен класс RandomAccessFile?](#28-Зачем-нужен-класс-RandomAccessFile)

[29. Данные в каком виде можно считывать байтовыми и символьными потоками?](#29-Данные-в-каком-виде-можно-считывать-байтовыми-и-символьными-потоками)

[30. Что такое сокет?](#30-Что-такое-сокет)

[31. Какие виды сокетов есть в Java? С каким протоколом они работают?](#31-Какие-виды-сокетов-есть-в-Java-С-каким-протоколом-они-работают)

[32. Как отправить через сокет сообщение?](#32-Как-отправить-через-сокет-сообщение)

[33. Что такое логирование?](#33-Что-такое-логирование)

[34. Какие уровни логирования вы знаете?](#34-Какие-уровни-логирования-вы-знаете)

[35. Какая библиотека для логирования используется в курсе? Как ее настроить?](#35-Какая-библиотека-для-логирования-используется-в-курсе-Как-ее-настроить)

[36. Опишите из каких элементов состоит формат JSON](#36-Опишите-из-каких-элементов-состоит-формат-JSON)

[37. Как преобразовать POJO в или из json?](#37-Как-преобразовать-POJO-в-или-из-json)

[38. Опишите из каких элементов состоит формат XML](#38-Опишите-из-каких-элементов-состоит-формат-XML)

[39. Как преобразовать POJO в или из xml?](#39-Как-преобразовать-POJO-в-или-из-xml)

[40. Что такое сериализация, десериализация?](#40-Что-такое-сериализация-десериализация)

[41. Что такое регулярные выражения? Зачем они нужны?](#41-Что-такое-регулярные-выражения-Зачем-они-нужны)

[42. Как создать регулярное выражение в Java?](#42-Как-создать-регулярное-выражение-в-Java)

[43. Что такое метасимволы? Для чего они применяются в регулярных выражениях?](#43-Что-такое-метасимволы-Для-чего-они-применяются-в-регулярных-выражениях)

# 1. Что такое поток ввода-вывода?

Это абстракция для потребления или поставки данных. Потоки ввода-вывода связаны с физическим устройством через базовую
систему ввода-вывода в Java. Благодаря абстракции потоков ввода-вывода все потоки ведут себя одинаково независимо от
физического устройства (клавиатуры, консоли, файлов, сети). С помощью одних и тех же классов и методов ввода-вывода
можно принимать данные с разнотипных устройств и передавать их также в разнотипные устройства,
не задумываясь о реализации. Например, принять данные с клавиатуры и сохранить в файл, либо принять данные
из сети и вывести на консоль. Потоки ввода-вывода избавляют нас от необходимости разбираться в отличиях
ввода с клавиатуры или из файла, вывода на консоль или в файл и т.д. Таким образом, цель создания
IO API - абстрактный доступ к вводу-выводу, чтобы не зависеть от подробностей реализации физических устройств.

[К оглавлению](#IO)

# 2. Что такое Java IO?

Java IO — это классическая модель ввода-вывода, основанная на потоках (streams). Она появилась в первых версиях Java и
используется для работы с файлами, сетью и другими источниками данных. Используется потокоориентированный подход.
Данный подход организует чтение из потока или запись в поток последовательно по несколько байт в один момент времени.
Данные просто передаются из одного места в другое. Операции чтения/записи блокируют поток выполнения до завершения.

+ InputStream и OutputStream — для работы с байтами.
+ Reader и Writer — для работы с символами (текстом).

![IO hierarchy](https://github.com/itlazykin/answers_to_exam_questions/blob/main/main/resources/java.IO.png)

Для разных типов данных существуют разные реализации классов

| _                | Byte Based                            | _                                   | Character Based                   | _                           |
|------------------|---------------------------------------|-------------------------------------|-----------------------------------|-----------------------------|
| _                | Input                                 | Output                              | Input                             | Output                      |
| Basic            | InputStream                           | OutputStream                        | Reader / InputStreamReader        | Writer / OutputStreamWriter |
| Arrays           | ByteArrayInputStream                  | ByteArrayOutputStream               | CharArrayReader                   | CharArrayWriter             |
| Files            | FileInputStream / RandomAccessFile    | FileOutputStream / RandomAccessFile | FileReader                        | FileWriter                  |
| Pipes            | PipedInputStream                      | PipedOutputStream                   | PipedReader                       | PipedWriter                 |
| Buffering        | BufferedInputStream                   | BufferedOutputStream                | BufferedReader                    | BufferedWriter              |
| Filtering        | FilterInputStream                     | FilterOutputStream                  | FilterReader                      | FilterWriter                |
| Parsing          | PushbackInputStream / StreamTokenizer | _                                   | PushbackReader / LineNumberReader | _                           |
| Strings          | _                                     | _                                   | StringReader                      | StringWriter                |
| Data             | DataInputStream                       | DataOutputStream                    | _                                 | _                           |
| Data - Formatted | _                                     | PrintStream                         | _                                 | PrintWriter                 |
| Objects          | ObjectInputStream                     | ObjectOutputStream                  | _                                 | _                           |

[К оглавлению](#IO)

# 3. Что такое Java NIO?

Новая система Java NIO API использует буферориентированный подход.
Данный подход организует чтение и запись данных с помощью их загрузки в специальные буферы, внутри которых можно
перемещаться по данным вперед и назад, тем самым обеспечивается гибкость обработки данных.

[К оглавлению](#IO)

# 4. Что такое NIO 2?

В Java 7 система ввода-вывода NIO была значительно расширена (данное обновление также называют NIO.2).
Были добавлены несколько пакетов и классов, направленных на расширение возможностей применения системы ввода-вывода NIO.
Отдельно можно выделить пакет java.nio.file, его интерфейс Path и классы Paths, Files, которые расширяют возможности
манипуляции с файлами (файловый ввод-вывод).

1. Классы `Path` и `Paths`: `Path` представляет путь к файлу или директории в файловой системе, а `Paths` предоставляет
   методы для создания экземпляров класса `Path`.

2. Улучшенные операции с файлами: NIO.2 включает более удобные методы для чтения, записи и манипулирования файлами.
   Например, можно скопировать файлы с помощью метода `Files.copy()`, переименовать или удалить файлы, а также
   манипулировать атрибутами файлов.

3. Улучшенная поддержка символических ссылок: NIO.2 предоставляет классы для создания и манипуляции символическими
   ссылками, такие как `LinkOptions` и `Files.createSymbolicLink()`.

4. Поддержка чтения и записи метаданных файлов: NIO.2 предоставляет класс `BasicFileAttributes`, который содержит
   информацию о файле, такую как дата создания, последнего доступа, последней модификации и т. д.

5. Асинхронные операции ввода-вывода: NIO.2 поддерживает асинхронные операции чтения и записи файлов, позволяя
   эффективно использовать ресурсы системы и обрабатывать множество операций одновременно.

IO, NIO и NIO.2 - это не замены друг другу. Скорее они дополняют друг друга для предоставления более широких возможностей работы системы ввода-вывода Java.


[К оглавлению](#IO)

# 5. Что такое Scanner?

Это класс в Java, который упрощает чтение и парсинг данных из различных источников, таких как консоль, файлы или строки. Он предоставляет удобные методы для чтения примитивных типов данных (int, double, boolean) и строк.

[К оглавлению](#IO)

# 6. Как работает Scanner внутри?

В качестве источника данных Scanner принимает любой вид данных, включая Reader, InputStream, File для java.io и Readable, Path для java.util.nio.
Также можно задать источник в виде строки String.

1)Читает данные и сохраняет их в буфер (временное хранилище).

2)Разбивает данные на части с помощью разделителя (по умолчанию — пробел).

3)Преобразует эти части в нужный тип (число, строку и т.д.) с помощью методов, например nextInt(), nextDouble(), nextLine()."

[К оглавлению](#IO)

# 7. Какие базовые методы существуют в Scanner?

+ next() — считывает следующий токен (слово).
+ nextLine() — считывает всю строку.
+ nextInt() — считывает целое число.
+ nextDouble() — считывает число с плавающей точкой.
+ nextBoolean() — считывает булево значение (true или false).
+ hasNext() — проверяет, есть ли ещё токены (данные) для чтения.
+ useDelimiter(String pattern) — позволяет задать разделитель, по которому будет происходить разбиение текста на
  токены (по умолчанию — пробелы и переносы строк)

[К оглавлению](#IO)

# 8. Что такое байтовый поток? Как он реализован внутри?

Байтовые потоки предоставляют средства ввода-вывода отдельных байтов, например, чтения и записи двоичных данных.

В основе байтовых потоков лежат абстрактные классы InputStream и OutputStream (потоки ввода и вывода соответственно).
Каждый из этих классов имеет свои классы-реализации, которые учитывают особенности разных устройств (файлов на диске,
сетевых соединений, буферов памяти и т.д.).

Основные классы-реализации InputStream (потоки ввода):

    - ByteArrayInputStream - читает байты из массива

    - FileInputStream - читает данные из файла

    - ObjectInputStream - поток ввода объектов

    - PipedInputStream - канал ввода

    - FilterInputStream - реализует класс InputStream. От него реализуются следующие 3 класса:

            - BufferedInputStream - буферизированный поток ввода

            - DataInputStream - читает данные примитивных типов

            - PushbackInputStream - поток ввода, поддерживающий возврат одного байта обратно в поток ввода

Основные классы-реализации OutputStream (потоки вывода):

    - ByteArrayOutputStream - записывает байты в массив

    - FileOutputStream - записывает данные в файл

    - ObjectOutputStream - поток вывода объектов

    - PipedOutputStream - канал вывода

    - PrintStream - поток вывода, содержащий методы print() и println()

    - FilterOutputStream - реализует класс OutputStream. От него реализуются следующие 2 класса:

            - BufferedOutputStream - буферизированный поток вывода

            - DataOutputStream - записывает данные примитивных типов



Важно! Все классы, имеющие в названии InputStream/OutputStream читают/пишут данные побайтово.

```java
import java.io.FileInputStream;
import java.io.IOException;

public class InputStreamExample {
    public static void main(String[] args) {
        try (FileInputStream inputStream = new FileInputStream("example.txt")) {
            int byteData;
            while ((byteData = inputStream.read()) != -1) {
                System.out.print((char) byteData); // Преобразование байта в символ
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

```java
import java.io.FileOutputStream;
import java.io.IOException;

public class OutputStreamExample {
    public static void main(String[] args) {
        try (FileOutputStream outputStream = new FileOutputStream("output.txt")) {
            String data = "Hello, world!";
            outputStream.write(data.getBytes()); // Запись строки в файл
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

[К оглавлению](#IO)

# 9. Что такое символьный поток. Как он реализован внутри?

Символьные потоки предоставляют средства ввода-вывода отдельных символов. В них применяется кодировка Юникод.
Читать данные по байтам в большинстве случаев неудобно, поэтому были введены символьные потоки, которые во многих случаях более эффективны, чем байтовые, так как считывают целиком символы, а не байты.
Но на низком уровне весь ввод-вывод в java все равно имеет байтовую организацию.

В основе символьных потоков лежат абстрактные классы Reader и Writer (потоки ввода и вывода соответственно).
Каждый из этих классов также имеет свои классы-реализации, которые учитывают особенности разных устройств (файлов на диске, сетевых соединений, буферов памяти и т.д.).

Основные классы-реализации Reader (потоки ввода символов):

    - BufferedReader - буферизированный поток ввода символов

    - CharArrayReader - читает символы из массива

    - PipedReader - канал ввода

    - StringReader - читает символы из строки

    - FilterReader - фильтрованный поток чтения. От этого класса наследуется класс PushbackReader:

            - PushbackReader - поток ввода, позволяющий вернуть считанные символы обратно в поток ввода

    - InputStreamReader - преобразует байты в символы. От этого класса наследуется класс FileReader:

            - FileReader - читает символы из файла


Основные классы-реализации Writer (потоки вывода символов):

    - BufferedWriter - буферизированный поток вывода символов

    - CharArrayWriter - записывает символы в массив

    - PipedWriter - канал вывода

    - StringWriter - записывает символы в строку

    - FilterWriter - фильтрованный поток записи.

    - PrintWriter - поток вывода, содержащий методы print() и println()

    - OutputStreamWriter - преобразует символы в байты. От этого класса наследуется класс FileWriter:

            - FileWriter - записывает символы в файл

```java
import java.io.FileReader;
import java.io.IOException;

public class FileReaderExample {
    public static void main(String[] args) {
        try (FileReader reader = new FileReader("example.txt")) {
            int character;
            while ((character = reader.read()) != -1) {
                System.out.print((char) character);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

```java
import java.io.FileWriter;
import java.io.IOException;

public class FileWriterExample {
    public static void main(String[] args) {
        try (FileWriter writer = new FileWriter("output.txt")) {
            writer.write("Hello, world!");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

#### Как символьный поток работает внутри?

Символьные потоки используют буферизированные массивы символов для чтения и записи данных, обеспечивая работу с текстом
в кодировке Unicode.
   
[К оглавлению](#IO)

# 10. Что такое буферизированный поток?

Буферизированный поток - это стандартный поток, к которому добавлен специальный буфер в памяти, который увеличивает производительность чтения и записи.
Обращение к ресурсу при чтении/записи - это очень затратный процесс, поэтому чем меньше обращений к ресурсу - тем лучше.
Буферизированные потоки - это обёртки обычных потоков с буфером.


```java
import java.io.BufferedInputStream;
import java.io.FileInputStream;
import java.io.IOException;

public class BufferedInputStreamExample {
    public static void main(String[] args) {
        try (BufferedInputStream bis = new BufferedInputStream(new FileInputStream("example.txt"))) {
            int data;
            while ((data = bis.read()) != -1) {
                System.out.print((char) data);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

```java
import java.io.BufferedOutputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class BufferedOutputStreamExample {
    public static void main(String[] args) {
        try (BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("output.txt"))) {
            String content = "Hello, World!";
            bos.write(content.getBytes());
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

Символьные буферизированные потоки:

+ `BufferedReader` — буферизированный поток для чтения символов.
+ `BufferedWriter` — буферизированный поток для записи символов.

```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class BufferedReaderExample {
    public static void main(String[] args) {
        try (BufferedReader br = new BufferedReader(new FileReader("example.txt"))) {
            String line;
            while ((line = br.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

```java
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;

public class BufferedWriterExample {
    public static void main(String[] args) {
        try (BufferedWriter bw = new BufferedWriter(new FileWriter("output.txt"))) {
            bw.write("Hello, Buffered World!");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

[К оглавлению](#IO)

# 11. Какие классы-обёртки позволяют ускорить чтение или запись за счет использования буфера?

Буферное побайтовое чтение/запись реализовано классами BufferedInputStream и BufferedOutputStream.
Буферное посимвольное чтение/запись реализовано классами BufferedReader и BufferedWriter.

Все buffered* классы являются обёртками и не могут существовать сами по себе.
При создании объектов этих классов в их конструкторы нужно передавать объекты классов-реализаций InputStream/OutputStream.
Могут быть и цепочки обёрток, но в корне всегда должен быть байтовый или символьный поток.

```java
FileInputStream fileInput = new FileInputStream("file.txt");
BufferedInputStream bufferedInput = new BufferedInputStream(fileInput);
```

```java
FileOutputStream fileOutput = new FileOutputStream("output.txt");
BufferedOutputStream bufferedOutput = new BufferedOutputStream(fileOutput);
```

```java
FileReader fileReader = new FileReader("file.txt");
BufferedReader bufferedReader = new BufferedReader(fileReader);
```

```java
FileWriter fileWriter = new FileWriter("output.txt");
BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);
```

[К оглавлению](#IO)

# 12. Как осуществляется ввод и вывод из командной строки?

System.out - ссылается на стандартный поток вывода (консоль).

System.in - ссылается на стандартный поток ввода (клавиатура).

System.err - ссылается на стандартный поток вывода ошибок (консоль).


```java
import java.util.Scanner;

public class ConsoleInputExample {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);  // Создаём объект Scanner для чтения данных из System.in

        System.out.println("Введите ваше имя: ");
        String name = scanner.nextLine();  // Считываем строку, введённую пользователем

        System.out.println("Введите ваш возраст: ");
        int age = scanner.nextInt();  // Считываем число (целое) от пользователя

        System.out.println("Привет, " + name + "! Тебе " + age + " лет.");

        scanner.close();  // Закрываем Scanner для освобождения ресурсов
    }
}
```

```java
public class ConsoleOutputExample {
    public static void main(String[] args) {
        System.out.println("Hello, World!");  // Вывод строки с переводом строки в конце
        System.out.print("Введите число: ");  // Вывод строки без перевода строки
        System.out.printf("Число с форматированием: %d%n", 42);  // Форматированный вывод
    }
}
```

```java
import java.io.IOException;

public class SystemInExample {
    public static void main(String[] args) {
        System.out.println("Введите символ: ");
        try {
            int input = System.in.read();  // Чтение байта из входного потока
            System.out.println("Вы ввели: " + (char) input);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

[К оглавлению](#IO)

# 13. Что такое класс Console? Расскажите его АПИ.

Класс Console предназначен для работы с консолью - командной строкой Windows или терминалом Linux/MacOS и упрощает работу с ними.
Класс Console определён в пакете java.io.

Доступ к консоли (командной строке) можно получить только из самой командной строки.
Попытка получить объект консоли в любой среде разработки вернёт null, поэтому полученный объект требуется проверять на null.

Методы объекта Console:
- `readLine()`: Читает строку из командной строки пользователя и возвращает ее.
- `readPassword()`: Читает пароль (символы не отображаются на экране) из командной строки пользователя и возвращает его в виде массива символов char[].
- `format()`: Осуществляет форматированный вывод в командную строку с использованием форматной строки и дополнительных аргументов.
- `writer()`: Получает объект PrintWriter для вывода сообщений в командную строку.
- `flush()`: Сбрасывает все данные из выводного буфера в командную строку.
- `printf()`: Осуществляет форматированный вывод в командную строку, аналогичный методу format().

```java
Console console = System.console();
if(console ==null){
        System.out.println("Консоль недоступна.");
    return;
}

Пример создания объекта Console
```

```java
Console console = System.console();
String name = console.readLine("Введите ваше имя: ");
System.out.println("Привет, "+name +"!");
```

```java
Console console = System.console();
char[] password = console.readPassword("Введите пароль: ");
// Обработка пароля...

Пароль считываетсякак массив char[],а не
как строка(String), чтобы минимизировать риск утечки
данных,поскольку char[] можно быстро о бнулить после использования .
```

```java
console.printf("Привет, %s! Твой возраст: %d%n","Денчик",35);
```

```java
Console console = System.console();
Reader reader = console.reader();
// Чтение данных с использованием Reader

Пример использования Reader
```

```java
Console console = System.console();
PrintWriter writer = console.writer();
writer.println("Это пример вывода через PrintWriter.");

Пример использования PrintWriter
```

```java
Пример программы,которая использует Console
для ввода данных и безопасного ввода пароля

import java.io.Console;

public class ConsoleExample {
    public static void main(String[] args) {
        Console console = System.console();

        if (console == null) {
            System.out.println("Консоль недоступна.");
            return;
        }

        // Считывание имени
        String username = console.readLine("Введите имя пользователя: ");

        // Считывание пароля
        char[] password = console.readPassword("Введите пароль: ");

        // Вывод отформатированного сообщения
        console.printf("Добро пожаловать, %s!%n", username);

        // Обнуление массива пароля после использования
        java.util.Arrays.fill(password, ' ');
    }
}
```

[К оглавлению](#IO)

# 14. Что такое поток данных? Data stream.

Класс DataOutputStream позволяет записывать примитивные типы данных, а также строковые значения в байтовом представлении,
а класс DataInputStream позволяет считывать примитивы из их байтового представления.

Классы DataInputStream и DataOutputStream реализуют интерфейсы DataInput и DataOutput соответственно.
Эти интерфейсы содержат методы, с помощью которых можно читать и записывать примитивы и строки в поток.
Например, writeBoolean(), writeDouble(), readBoolean(), readDouble() и т.д.
Эти методы преобразуют значения примитивных типов в последовательность байтов и наоборот.
Таким образом упрощается хранение данных в двоичной форме в файлах.

```java
Пример использования DataInputStream и DataOutputStream

import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class DataStreamExample {
    public static void main(String[] args) {
        // Запись данных в файл с использованием DataOutputStream
        try (DataOutputStream dataOut = new DataOutputStream(new FileOutputStream("data.bin"))) {
            dataOut.writeInt(123);         // Записываем целое число
            dataOut.writeDouble(45.67);    // Записываем число с плавающей точкой
            dataOut.writeBoolean(true);    // Записываем логическое значение
            dataOut.writeUTF("Привет!");   // Записываем строку в формате UTF-8
        } catch (IOException e) {
            e.printStackTrace();
        }

        // Чтение данных из файла с использованием DataInputStream
        try (DataInputStream dataIn = new DataInputStream(new FileInputStream("data.bin"))) {
            int number = dataIn.readInt();         // Чтение целого числа
            double decimal = dataIn.readDouble();  // Чтение числа с плавающей точкой
            boolean flag = dataIn.readBoolean();   // Чтение логического значения
            String text = dataIn.readUTF();        // Чтение строки в формате UTF-8

            System.out.println("Целое число: " + number);
            System.out.println("Число с плавающей точкой: " + decimal);
            System.out.println("Логическое значение: " + flag);
            System.out.println("Строка: " + text);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```

[К оглавлению](#IO)

# 15. Что такое поток объектов, Object stream.

Потоки объектов представлены в пакете java.io классами ObjectInputStream и ObjectOutputStream. ObjectOutputStream превращает объект в его байтовое представление.
ObjectInputStream восстанавливает объект из байтового представления в обычное. Эти процессы называются сериализацией и десериализацией соответственно.
С помощью этих операций можно сохранить объект (состояние объекта) в виде последовательности байт, удобной для передачи по сети, и восстановить эту последовательность байт обратно в объект, например, на другом компьютере.


```java
Конструктор:

ObjectOutputStream(OutputStream out)

Создаёт ObjectOutputStream, который записывает данные
в указанный OutputStream
```

```java
Пример использования ObjectOutputStream

import java.io.FileOutputStream;
import java.io.ObjectOutputStream;
import java.io.IOException;

public class ObjectOutputStreamExample {
    public static void main(String[] args) {
        try (FileOutputStream fileOut = new FileOutputStream("objectData.bin");
             ObjectOutputStream objOut = new ObjectOutputStream(fileOut)) {

            MyClass myObject = new MyClass("Пример объекта", 42);
            objOut.writeObject(myObject); // Сериализация объекта
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```

```java
Конструктор

ObjectInputStream(InputStream in)

Создаёт ObjectInputStream, который считывает данные
из указанного InputStream .
```


```java
Пример использования ObjectInputStream

import java.io.FileInputStream;
import java.io.ObjectInputStream;
import java.io.IOException;

public class ObjectInputStreamExample {
    public static void main(String[] args) {
        try (FileInputStream fileIn = new FileInputStream("objectData.bin");
             ObjectInputStream objIn = new ObjectInputStream(fileIn)) {

            MyClass myObject = (MyClass) objIn.readObject(); // Десериализация объекта
            System.out.println(myObject);
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}
```

```java
Пример полного кода с сериализацией и десериализацией

import java.io.*;

public class SerializationExample {
    public static void main(String[] args) {
        // Сериализация объекта
        try (FileOutputStream fileOut = new FileOutputStream("example.bin");
             ObjectOutputStream objOut = new ObjectOutputStream(fileOut)) {

            Person person = new Person("Денчик", 35);
            objOut.writeObject(person); // Сериализация
        } catch (IOException e) {
            e.printStackTrace();
        }

        // Десериализация объекта
        try (FileInputStream fileIn = new FileInputStream("example.bin");
             ObjectInputStream objIn = new ObjectInputStream(fileIn)) {

            Person deserializedPerson = (Person) objIn.readObject(); // Десериализация
            System.out.println("Десериализованный объект: " + deserializedPerson);
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}

class Person implements Serializable {
    private static final long serialVersionUID = 1L; // Идентификатор версии класса
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }
}
```

[К оглавлению](#IO)

# 16. Что такое Path? Как он реализуется на разных ОС?

Интерфейс Path определен в пакете java.nio.file, замена File.
Path - это усовершенствованная модель File.

```java
Path path = FileSystems.getDefault().getPath("logs", "access.log");
BufferedReader reader = Files.newBufferedReader(path, StandardCharsets.UTF_8);
```

В параметры метода getPath() передаются части пути отдельными строками.
При создании пути, из этих частей программой будет определен разделитель с помощью метода FileSystem.getSeparator(), и с помощью этого разделителя будет собрана строка.
В данном случае будет определен разделитель той ОС, в которой выполняется программа.

[К оглавлению](#IO)

# 17. Как получить список файлов?

io:

```java
File target = new File("src/main/java/ru/job4j/io/files");
File[] listFiles = target.listFiles();
for (File f : listFiles) {
    System.out.println(f);
}
```

nio:

Нужно использовать интерфейс FileVisitor.
Интерфейс FileVisitor имеет 4 метода. Нас будет интересовать только visitFile. Java последовательно передает в него файлы

```java
Path start = Paths.get(".");
Files.walkFileTree(start, new PrintFiles());
```

[К оглавлению](#IO)

# 18. Как проверить что файловая сущность является файлом или папкой?

+ File: Используйте методы isFile() и isDirectory() для простых задач проверки.

```java
import java.io.File;

public class FileCheckExample {
    public static void main(String[] args) {
        // Создание объекта File для проверки
        File file = new File("путь/к/вашему/файлу_или_папке");

        // Проверка, является ли это файлом
        if (file.isFile()) {
            System.out.println("Это файл.");
        } else if (file.isDirectory()) {
            System.out.println("Это директория.");
        } else {
            System.out.println("Это несуществующая файловая сущность.");
        }
    }
}
```

+ Path и Files: Используйте методы Files.isRegularFile() и Files.isDirectory() для более мощного и современного подхода
  к проверке файловых сущностей.

```java
import java.nio.file.*;
import java.io.IOException;

public class PathCheckExample {
    public static void main(String[] args) {
        // Создание объекта Path для проверки
        Path path = Paths.get("путь/к/вашему/файлу_или_папке");

        try {
            // Проверка, является ли это файлом
            if (Files.isRegularFile(path)) {
                System.out.println("Это файл.");
            } else if (Files.isDirectory(path)) {
                System.out.println("Это директория.");
            } else {
                System.out.println("Это несуществующая файловая сущность или специальный файл.");
            }
        } catch (IOException e) {
            System.out.println("Ошибка при проверке пути: " + e.getMessage());
        }
    }
}
```

+ В новых проектах предпочтительно использовать API java.nio.file, так как он предоставляет более продвинутые и удобные
  возможности для работы с файловой системой.

[К оглавлению](#IO)

# 19. Как удалить файл?

Класс File предоставляет метод delete(), который удаляет файл или пустую директорию.

```java
import java.io.File;

public class DeleteFileExample {
    public static void main(String[] args) {
        // Создание объекта File для файла, который нужно удалить
        File file = new File("путь/к/вашему/файлу.txt");

        // Удаление файла
        if (file.delete()) {
            System.out.println("Файл успешно удалён.");
        } else {
            System.out.println("Не удалось удалить файл.");
        }
    }
}
```

Современный подход к удалению файла заключается в использовании Path и метода Files.delete() или Files.deleteIfExists()

```java
Пример с использованием Files.delete()

import java.nio.file.*;
import java.io.IOException;

public class DeleteFileWithPathExample {
    public static void main(String[] args) {
        // Создание объекта Path для файла, который нужно удалить
        Path path = Paths.get("путь/к/вашему/файлу.txt");

        try {
            // Удаление файла
            Files.delete(path);
            System.out.println("Файл успешно удалён.");
        } catch (NoSuchFileException e) {
            System.out.println("Файл не найден.");
        } catch (IOException e) {
            System.out.println("Ошибка при удалении файла: " + e.getMessage());
        }
    }
}

```

```java
Пример с использованием Files.deleteIfExists()

import java.nio.file.*;
import java.io.IOException;

public class DeleteFileIfExistsExample {
    public static void main(String[] args) {
        // Создание объекта Path для файла, который нужно удалить
        Path path = Paths.get("путь/к/вашему/файлу.txt");

        try {
            // Удаление файла, если он существует
            boolean isDeleted = Files.deleteIfExists(path);
            if (isDeleted) {
                System.out.println("Файл успешно удалён.");
            } else {
                System.out.println("Файл не найден.");
            }
        } catch (IOException e) {
            System.out.println("Ошибка при удалении файла: " + e.getMessage());
        }
    }
}
```

+ delete() в File и Files бросает исключение, если файл не найден, поэтому подходит для ситуаций, когда вы точно
  ожидаете, что файл существует.
+ deleteIfExists() полезен, когда файл может не существовать, и вам не нужно бросать исключение в таком случае.

[К оглавлению](#IO)

# 20. Как переместить файл?

До JDK 7 не было готовой возможности переместить файл в другую директорию, но есть 2 варианта как это можно сделать вручную:

- Если переместить нужно содержимое файла, то достаточно применить метод File.renameTo(), то есть просто переименовать его, тем самым достигая результата "перемещения" данных в файл с заданным именем.
  Имейте в виду, что этот метод работает не во всех файловых системах, как было указано ранее.

- Если требуется переместить файл в другую директорию, то нужно скопировать содержимое файла в новый файл в другой директории, после чего старый файл удалить.

Начиная с версии JDK 7 появилась возможность переместить файл с помощью метода move():

move(Path source, Path target, CopyOption... options)

```java
Пример с использованием File.renameTo()

import java.io.File;

public class MoveFileExample {
    public static void main(String[] args) {
        // Создание объекта File для файла, который нужно переместить
        File sourceFile = new File("путь/к/вашему/исходному_файлу.txt");
        // Новый путь, куда нужно переместить файл
        File destFile = new File("путь/к/новой/директории/файл.txt");

        // Перемещение файла
        if (sourceFile.renameTo(destFile)) {
            System.out.println("Файл успешно перемещён.");
        } else {
            System.out.println("Не удалось переместить файл.");
        }
    }
}

```

```java
import java.nio.file.*;
import java.io.IOException;

public class MoveFileWithPathExample {
    public static void main(String[] args) {
        // Создание объекта Path для исходного файла
        Path sourcePath = Paths.get("путь/к/вашему/исходному_файлу.txt");
        // Новый путь, куда нужно переместить файл
        Path targetPath = Paths.get("путь/к/новой/директории/файл.txt");

        try {
            // Перемещение файла
            Files.move(sourcePath, targetPath, StandardCopyOption.REPLACE_EXISTING);
            System.out.println("Файл успешно перемещён.");
        } catch (IOException e) {
            System.out.println("Ошибка при перемещении файла: " + e.getMessage());
        }
    }
}
```

```java
import java.nio.file.*;
import java.io.IOException;

public class MoveFileWithOptionsExample {
    public static void main(String[] args) {
        // Создание объекта Path для исходного файла
        Path sourcePath = Paths.get("путь/к/вашему/исходному_файлу.txt");
        // Новый путь, куда нужно переместить файл
        Path targetPath = Paths.get("путь/к/новой/директории/файл.txt");

        try {
            // Перемещение файла с заменой и атомарным перемещением
            Files.move(sourcePath, targetPath,
                    StandardCopyOption.REPLACE_EXISTING,
                    StandardCopyOption.ATOMIC_MOVE);
            System.out.println("Файл успешно перемещён с использованием атомарного перемещения.");
        } catch (IOException e) {
            System.out.println("Ошибка при перемещении файла: " + e.getMessage());
        }
    }
}
```

[К оглавлению](#IO)

# 21. Как управлять атрибутами файла?

В Java управление атрибутами файла (такими как дата создания, права доступа и другие метаданные) осуществляется с
помощью API java.nio.file. В частности, используются классы Files, Path, и различные интерфейсы из пакета
java.nio.file.attribute.

1. Чтение базовых атрибутов файла
   Для чтения базовых атрибутов (дата создания, последняя модификация и т.д.) можно использовать интерфейс
   BasicFileAttributes с помощью метода Files.readAttributes().

```java
import java.nio.file.*;
import java.nio.file.attribute.*;
import java.io.IOException;

public class BasicFileAttributesExample {
    public static void main(String[] args) {
        // Создание объекта Path для файла
        Path path = Paths.get("путь/к/вашему/файлу.txt");

        try {
            // Чтение базовых атрибутов файла
            BasicFileAttributes attributes = Files.readAttributes(path, BasicFileAttributes.class);

            System.out.println("Дата создания: " + attributes.creationTime());
            System.out.println("Последняя модификация: " + attributes.lastModifiedTime());
            System.out.println("Размер файла: " + attributes.size() + " байт");
            System.out.println("Является ли это директорией: " + attributes.isDirectory());
        } catch (IOException e) {
            System.out.println("Ошибка при чтении атрибутов файла: " + e.getMessage());
        }
    }
}
```

2. Изменение базовых атрибутов файла
   Для изменения атрибутов, таких как время последней модификации, используется метод Files.setAttribute().

```java
import java.nio.file.*;
import java.io.IOException;
import java.nio.file.attribute.FileTime;
import java.time.Instant;

public class SetFileAttributeExample {
    public static void main(String[] args) {
        // Создание объекта Path для файла
        Path path = Paths.get("путь/к/вашему/файлу.txt");

        try {
            // Установка времени последней модификации на текущее время
            FileTime newTime = FileTime.from(Instant.now());
            Files.setAttribute(path, "basic:lastModifiedTime", newTime);

            System.out.println("Время последней модификации изменено.");
        } catch (IOException e) {
            System.out.println("Ошибка при изменении атрибутов файла: " + e.getMessage());
        }
    }
}
```

3. Управление правами доступа
   Для управления правами доступа в Java существует интерфейс PosixFileAttributes и класс PosixFilePermissions. Они
   позволяют работать с POSIX-совместимыми правами доступа (только на UNIX-подобных системах).

```java
import java.nio.file.*;
import java.nio.file.attribute.*;
import java.io.IOException;

public class FilePermissionsExample {
    public static void main(String[] args) {
        // Создание объекта Path для файла
        Path path = Paths.get("путь/к/вашему/файлу.txt");

        try {
            // Установка прав доступа (только для UNIX-подобных систем)
            Set<PosixFilePermission> perms = PosixFilePermissions.fromString("rwxr-x---");
            Files.setPosixFilePermissions(path, perms);

            System.out.println("Права доступа изменены.");
        } catch (UnsupportedOperationException e) {
            System.out.println("POSIX права не поддерживаются на данной системе.");
        } catch (IOException e) {
            System.out.println("Ошибка при изменении прав доступа: " + e.getMessage());
        }
    }
}
```

4. Чтение и изменение пользовательских атрибутов (xattr)
   Java позволяет работать с пользовательскими атрибутами, такими как метки или заметки, которые можно добавлять к
   файлам на поддерживаемых файловых системах. Для этого используется метод Files.getAttribute() и Files.setAttribute().

```java
import java.nio.file.*;
import java.io.IOException;

public class UserDefinedFileAttributesExample {
    public static void main(String[] args) {
        // Создание объекта Path для файла
        Path path = Paths.get("путь/к/вашему/файлу.txt");

        try {
            // Установка пользовательского атрибута
            String attributeName = "user.comment";
            String comment = "Это тестовый файл.";
            Files.setAttribute(path, attributeName, comment);

            // Чтение пользовательского атрибута
            String retrievedComment = (String) Files.getAttribute(path, attributeName);
            System.out.println("Пользовательский комментарий: " + retrievedComment);
        } catch (IOException e) {
            System.out.println("Ошибка при работе с пользовательскими атрибутами: " + e.getMessage());
        }
    }
}
```

5. Проверка и удаление атрибутов

+ Для проверки существования атрибута можно использовать метод Files.getAttribute().
+ Для удаления атрибута используется метод Files.setAttribute() с null значением для некоторых типов атрибутов, либо с
  использованием соответствующих методов управления правами.
  ####Рекомендации по использованию:
+ BasicFileAttributes — используйте для чтения базовых атрибутов (создание, модификация и т.д.).
+ PosixFileAttributes — подходит для управления правами на UNIX-подобных системах.
+ Пользовательские атрибуты — используйте для добавления меток или комментариев к файлам, если это поддерживается
  файловой системой.
+ Методы Files.getAttribute() и Files.setAttribute() позволяют управлять атрибутами файлов на более низком уровне и
  поддерживают различные типы атрибутов.

[К оглавлению](#IO)

# 22. Как создать файл?

Создать файл в Java можно несколькими способами с использованием классов File из пакета java.io и Files из пакета
java.nio.file. Каждый из этих методов имеет свои особенности и может быть применён в зависимости от ситуации

1. Использование класса File (пакет java.io)
   Старый, но простой способ создать файл — это использовать класс File. Метод createNewFile() позволяет создать новый
   файл, если его ещё нет в указанной директории.

```java
import java.io.File;
import java.io.IOException;

public class CreateFileExample {
    public static void main(String[] args) {
        // Создание объекта File для нового файла
        File file = new File("путь/к/новому_файлу.txt");

        try {
            // Создание нового файла
            if (file.createNewFile()) {
                System.out.println("Файл успешно создан: " + file.getName());
            } else {
                System.out.println("Файл уже существует.");
            }
        } catch (IOException e) {
            System.out.println("Ошибка при создании файла: " + e.getMessage());
        }
    }
}
```

2. Использование класса Files (пакет java.nio.file)
   Современный и более предпочтительный способ создания файла — это использование класса Files вместе с интерфейсом
   Path. Метод Files.createFile() создаёт файл и выбрасывает исключение, если файл уже существует.

```java
import java.nio.file.*;
import java.io.IOException;

public class CreateFileWithPathExample {
    public static void main(String[] args) {
        // Создание объекта Path для нового файла
        Path path = Paths.get("путь/к/новому_файлу.txt");

        try {
            // Создание нового файла
            Files.createFile(path);
            System.out.println("Файл успешно создан: " + path.getFileName());
        } catch (FileAlreadyExistsException e) {
            System.out.println("Файл уже существует.");
        } catch (IOException e) {
            System.out.println("Ошибка при создании файла: " + e.getMessage());
        }
    }
}
```

3. Создание временного файла Если вам нужно создать временный файл, который не должен сохраняться после завершения
   программы, можно использовать метод Files.createTempFile().

```java
import java.nio.file.*;
import java.io.IOException;

public class CreateTempFileExample {
    public static void main(String[] args) {
        try {
            // Создание временного файла с префиксом "temp" и суффиксом ".txt"
            Path tempFile = Files.createTempFile("temp", ".txt");
            System.out.println("Временный файл создан: " + tempFile.toAbsolutePath());
        } catch (IOException e) {
            System.out.println("Ошибка при создании временного файла: " + e.getMessage());
        }
    }
}
```

4. Создание файла с указанием прав доступа (только для UNIX-систем)
   Если нужно создать файл с определёнными правами доступа, это можно сделать с помощью опций FileAttribute в
   Files.createFile().

```java
import java.nio.file.*;
import java.nio.file.attribute.*;
import java.io.IOException;
import java.util.Set;

public class CreateFileWithPermissionsExample {
    public static void main(String[] args) {
        Path path = Paths.get("путь/к/новому_файлу.txt");

        try {
            // Установка прав доступа
            Set<PosixFilePermission> permissions = PosixFilePermissions.fromString("rw-r-----");
            FileAttribute<Set<PosixFilePermission>> fileAttributes = PosixFilePermissions.asFileAttribute(permissions);

            // Создание файла с заданными правами доступа
            Files.createFile(path, fileAttributes);
            System.out.println("Файл успешно создан с правами доступа: " + permissions);
        } catch (IOException e) {
            System.out.println("Ошибка при создании файла: " + e.getMessage());
        }
    }
}
```

#### Сравнение методов создания файла

+ File.createNewFile(): простой, но не самый надёжный способ. Может не работать на некоторых файловых системах, и
  отсутствует гибкость при установке прав доступа.
+ Files.createFile(): более современный способ с поддержкой обработки исключений и возможностью настройки прав доступа.
+ Files.createTempFile(): создаёт временный файл, который автоматически удаляется после завершения программы.

[К оглавлению](#IO)

# 23. Как создать директорию?

1. Использование класса File (пакет java.io) Старый, но всё ещё используемый способ создания директории — это метод
   mkdir() или mkdirs() класса File.

+ mkdir() — создаёт одну директорию. Вернёт false, если путь к директории не существует.
+ mkdirs() — создаёт всю структуру директорий, если какая-то часть пути отсутствует.

```java
import java.io.File;

public class CreateDirectoryExample {
    public static void main(String[] args) {
        // Создание объекта File для новой директории
        File directory = new File("путь/к/новой/директории");

        // Создание директории
        if (directory.mkdir()) {
            System.out.println("Директория успешно создана: " + directory.getPath());
        } else {
            System.out.println("Не удалось создать директорию.");
        }
    }
}

import java.io.File;

public class CreateDirectoriesExample {
    public static void main(String[] args) {
        // Создание объекта File для нескольких директорий
        File directories = new File("путь/к/нескольким/новым/директориям");

        // Создание всей структуры директорий
        if (directories.mkdirs()) {
            System.out.println("Структура директорий успешно создана: " + directories.getPath());
        } else {
            System.out.println("Не удалось создать структуру директорий.");
        }
    }
}

```

2. Использование класса Files (пакет java.nio.file) Современный и рекомендуемый способ создания директории — это
   использование класса Files вместе с интерфейсом Path.

+ Files.createDirectory(path) создаёт одну директорию и выбрасывает исключение IOException, если путь не существует или
  директория уже есть.
+ Files.createDirectories(path) создаёт всю структуру директорий, если какая-то часть пути отсутствует.

```java
import java.nio.file.*;
import java.io.IOException;

public class CreateDirectoryWithPathExample {
    public static void main(String[] args) {
        // Создание объекта Path для новой директории
        Path path = Paths.get("путь/к/новой/директории");

        try {
            // Создание директории
            Files.createDirectory(path);
            System.out.println("Директория успешно создана: " + path);
        } catch (IOException e) {
            System.out.println("Ошибка при создании директории: " + e.getMessage());
        }
    }
}

import java.nio.file .*;
        import java.io.IOException;

public class CreateDirectoriesWithPathExample {
    public static void main(String[] args) {
        // Создание объекта Path для нескольких директорий
        Path path = Paths.get("путь/к/нескольким/новым/директориям");

        try {
            // Создание всей структуры директорий
            Files.createDirectories(path);
            System.out.println("Структура директорий успешно создана: " + path);
        } catch (IOException e) {
            System.out.println("Ошибка при создании структуры директорий: " + e.getMessage());
        }
    }
}
```

[К оглавлению](#IO)

# 24. Как записать в файл?

1. Использование класса FileWriter для записи текстовых данных в файл.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FileWriterExample {
    public static void main(String[] args) {
        try (FileWriter writer = new FileWriter("example.txt", false)) { // false = перезаписать файл
            writer.write("Привет, мир!"); // Записываем строку в файл
            writer.write(System.lineSeparator()); // Переход на новую строку
            writer.write("Как дела?");
            System.out.println("Запись завершена.");
        } catch (IOException e) {
            System.out.println("Произошла ошибка: " + e.getMessage());
        }
    }
}

Аргумент false указывает, что файл будет перезаписан.
Если указать true, данные будут добавлены в конец файла.
В блоке try-with-resources ресурс закрывается автоматически.
```

2. Использование класса BufferedWriter, используется для буферизированной записи, что увеличивает производительность при
   записи больших объёмов данных.

```java
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;

public class BufferedWriterExample {
    public static void main(String[] args) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter("example.txt"))) {
            writer.write("Буферизированная запись.");
            writer.newLine(); // Добавляет новую строку
            writer.write("Это быстрее для больших файлов.");
            System.out.println("Запись завершена.");
        } catch (IOException e) {
            System.out.println("Произошла ошибка: " + e.getMessage());
        }
    }
}
```

3. PrintWriter упрощает запись строк, позволяя использовать знакомые методы вроде println().

````java
import java.io.PrintWriter;
import java.io.IOException;

public class PrintWriterExample {
    public static void main(String[] args) {
        try (PrintWriter writer = new PrintWriter("example.txt")) {
            writer.println("Привет, мир!"); // Записываем строку с переходом на новую строку
            writer.println("Запись упрощена.");
            System.out.println("Запись завершена.");
        } catch (IOException e) {
            System.out.println("Произошла ошибка: " + e.getMessage());
        }
    }
}
````

4. Использование класса Files (пакет java.nio.file). Современный способ, который позволяет работать с текстом и
   бинарными файлами.

```java
import java.nio.file.*;
import java.io.IOException;
import java.util.Arrays;

public class FilesWriteExample {
    public static void main(String[] args) {
        Path path = Paths.get("example.txt");

        try {
            Files.write(path, Arrays.asList("Привет, мир!", "Как дела?"), StandardOpenOption.CREATE);
            System.out.println("Запись завершена.");
        } catch (IOException e) {
            System.out.println("Произошла ошибка: " + e.getMessage());
        }
    }
}

Метод Files.write() принимает коллекцию строк для записи.
Аргумент StandardOpenOption.CREATE указывает, чтофайл нужно
создать, если его нет.
```

5. Использование класса DataOutputStream. Подходит для записи примитивных данных (int, double, char и т.д.) в бинарном
   формате.

```java
import java.io.DataOutputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class DataOutputStreamExample {
    public static void main(String[] args) {
        try (DataOutputStream dos = new DataOutputStream(new FileOutputStream("example.dat"))) {
            dos.writeInt(123); // Записываем число
            dos.writeDouble(45.67); // Записываем число с плавающей точкой
            dos.writeUTF("Привет!"); // Записываем строку
            System.out.println("Запись завершена.");
        } catch (IOException e) {
            System.out.println("Произошла ошибка: " + e.getMessage());
        }
    }
}
```

6. Использование класса ObjectOutputStream. Используется для записи объектов в файл (сериализация).

```java
import java.io.*;

public class ObjectOutputStreamExample {
    public static void main(String[] args) {
        try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("example.obj"))) {
            oos.writeObject("Привет, мир!"); // Сериализация строки
            oos.writeObject(123); // Сериализация числа
            System.out.println("Запись завершена.");
        } catch (IOException e) {
            System.out.println("Произошла ошибка: " + e.getMessage());
        }
    }
}

Класс записываемого объекта должен реализовать интерфейс Serializable .
```

[К оглавлению](#IO)

# 25. Как прочитать данные из файла?

1) java.io.FileInputStream

Создаём байтовый поток и через StringBuilder формируем текст

```java
try (FileInputStream in = new FileInputStream("data/input.txt")) {
            StringBuilder text = new StringBuilder();
            int read;
            while ((read = in.read()) != -1) {
                text.append((char) read);
            }
            System.out.println(text);
```

2) Scanner

```java
var scanner = new Scanner(new ByteArrayInputStream(data.getBytes()))
```

[К оглавлению](#IO)

# 26. Для чего нужны классы PrintStream и PrintWriter? В чем их различие?

PrintStream - используется для вывода данных в потоки вывода(консоль, файл и тд) с помощью методов print*() и write()

PrintWriter - используется для вывода текста в потоки вывода

Если нужно работать с текстовыми данными, то лучше использовать для этих целей PrintWriter, а если с байтовыми или смешанными данными - PrintStream.

Главное их отличие только в том, что PrintStream читает побайтово, а PrintWriter посимвольно, и выбирать тот или иной класс нужно в
зависимости от вида данных, с которым требуется работать.

```java
import java.io.FileOutputStream;
import java.io.PrintStream;
import java.io.IOException;

public class PrintStreamExample {
    public static void main(String[] args) {
        try (PrintStream ps = new PrintStream(new FileOutputStream("example.txt"))) {
            ps.println("Привет, мир!"); // Запись строки с переходом на новую строку
            ps.print(123); // Запись числа без перехода
            ps.printf(" Форматированное число: %.2f", 45.6789); // Форматированный вывод
        } catch (IOException e) {
            System.out.println("Ошибка при записи: " + e.getMessage());
        }
    }
}

println() добавляет символ новой строки после записи.
print() записывает данные без перехода на новую строку.
printf() позволяет форматировать строки с использованием шаблонов.
```

```java
import java.io.FileWriter;
import java.io.PrintWriter;
import java.io.IOException;

public class PrintWriterExample {
    public static void main(String[] args) {
        try (PrintWriter pw = new PrintWriter(new FileWriter("example.txt"))) {
            pw.println("Привет, мир!"); // Запись строки с переходом на новую строку
            pw.print(123); // Запись числа без перехода
            pw.printf(" Форматированное число: %.2f", 45.6789); // Форматированный вывод
        } catch (IOException e) {
            System.out.println("Ошибка при записи: " + e.getMessage());
        }
    }
}
```

| Критерий          | PrintStream                               | PrintWriter                               |
|-------------------|-------------------------------------------|-------------------------------------------|
| Работа с потоками | Использует OutputStream (байтовые потоки) | Использует Writer (символьные потоки)     |
| Тип данных        | Подходит для записи байтов и текста       | Оптимален для текстовых данных            |
| Поддержка Unicode | Может быть ограничена                     | Полная поддержка Unicode                  |
| Буферизация       | Не буферизирован                          | Часто буферизирован                       |
| Поток вывода      | System.out (наследуется)                  | Нужно явно указать поток (например, файл) |
| Исключения        | Игнорирует IOException                    | Игнорирует IOException                    |

[К оглавлению](#IO)

# 27. Что такое потоки байтовых массивов? Как они устроены?

ByteArrayInputStream и ByteArrayOutputStream.

Данные классы являются реализациями байтовых потоков (не обёртками) и позволяют читать данные из массива байтов и
записывать данные в массив байтов соответственно.

ByteArrayInputStream - это класс, позволяющий читать данные из байтового массива.
Он наследуется от класса InputStream и предоставляет методы для чтения байтов из массива.
При создании экземпляра ByteArrayInputStream передается массив данных, из которого будут читаться данные.
Затем можно использовать методы, такие как read(), read(byte[] buffer, int offset, int length), available() и skip(),
чтобы получить доступ к данным в массиве.

ByteArrayOutputStream - это класс, позволяющий записывать данные в байтовый массив.
Он наследуется от класса OutputStream и предоставляет методы для записи байтов во внутренний массив.
При создании экземпляра ByteArrayOutputStream необходимо указать начальный размер буфера, в котором будут храниться
данные.
Затем можно использовать методы, такие как write(int b), write(byte[] buffer, int offset, int length) и toByteArray(),
чтобы записать данные в массив и получить их в виде массива байтов.

Они позволяют использовать байтовые массивы как источники или приемники данных, что может быть полезным, например, при
работе с сетевыми протоколами или чтении и записи файлов в памяти.

```java
import java.io.ByteArrayInputStream;
import java.io.IOException;

public class ByteArrayInputStreamExample {
    public static void main(String[] args) {
        byte[] data = {65, 66, 67, 68}; // Байты для символов 'A', 'B', 'C', 'D'

        try (ByteArrayInputStream bais = new ByteArrayInputStream(data)) {
            int byteRead;
            while ((byteRead = bais.read()) != -1) { // Читаем байт за байтом
                System.out.println("Прочитано: " + (char) byteRead);
            }
        } catch (IOException e) {
            System.out.println("Ошибка: " + e.getMessage());
        }
    }
}

Ключевые методы:

read() — считывает следующий байт,возвращает -1, если достигнут конец.
reset() — возвращает указатель чтения в начало массива.
available() — возвращает количество байтов, доступных для чтения .
```

```java
import java.io.ByteArrayOutputStream;
import java.io.IOException;

public class ByteArrayOutputStreamExample {
    public static void main(String[] args) {
        try (ByteArrayOutputStream baos = new ByteArrayOutputStream()) {
            baos.write(65); // Записываем байт (символ 'A')
            baos.write(66); // Записываем байт (символ 'B')
            baos.write(67); // Записываем байт (символ 'C')

            byte[] result = baos.toByteArray(); // Извлекаем записанные байты

            System.out.println("Результат: " + new String(result)); // Преобразуем в строку
        } catch (IOException e) {
            System.out.println("Ошибка: " + e.getMessage());
        }
    }
}

Ключевые методы

write(int b) — записывает один байт.
write(byte[] b, int off, int len) — записывает часть массива.
toByteArray() — возвращает массив записанных байтов.
reset() — очищает буфер, позволяя начать запись заново.
```

#### Как устроены внутри?

`1. ByteArrayInputStream`

+ Хранит массив байтов в приватном поле.
+ Внутренний указатель (pos) отслеживает текущую позицию для чтения.
+ Метод read() возвращает текущий байт и сдвигает указатель вперед.

```java
public class ByteArrayInputStreamExample {
    private byte[] buffer;
    private int pos = 0;

    public ByteArrayInputStreamExample(byte[] buf) {
        this.buffer = buf;
    }

    public int read() {
        if (pos < buffer.length) {
            return buffer[pos++] & 0xFF; // Читаем байт и сдвигаем указатель
        } else {
            return -1; // Конец данных
        }
    }
}
```

`2. ByteArrayOutputStream`

+ Использует внутренний массив, который увеличивается при необходимости.
+ При достижении предела создается новый массив большего размера, а данные копируются.
+ После завершения записи данные можно извлечь с помощью метода toByteArray().

```java
public class ByteArrayOutputStreamExample {
    private byte[] buffer;
    private int size = 0;

    public ByteArrayOutputStreamExample() {
        this.buffer = new byte[32]; // Начальный размер
    }

    public void write(int b) {
        if (size == buffer.length) {
            expandBuffer();
        }
        buffer[size++] = (byte) b;
    }

    private void expandBuffer() {
        byte[] newBuffer = new byte[buffer.length * 2];
        System.arraycopy(buffer, 0, newBuffer, 0, buffer.length);
        buffer = newBuffer;
    }

    public byte[] toByteArray() {
        return java.util.Arrays.copyOf(buffer, size);
    }
}
```

[К оглавлению](#IO)

# 28. Зачем нужен класс RandomAccessFile?

Для одновременного чтения и записи файла.

В отличие от других классов-потоков, которые рассматриваются в этом разделе, класс RandomAccessFile не наследуется от
классов InputStream и OutputStream.
Вместо них он реализует интерфейсы DataInput и DataOutput, а также имеет свои методы для осуществления одновременного
чтения и записи файла.

Главная особенность класса RandomAccessFile - это возможность перемещаться по данным и читать только те данные, которые
нам нужны, вместо считывания файла целиком, а также записывать данные в указанное место (в начало, конец или
произвольно).

Для этого в классе RandomAccessFile определены следующие методы:

- seek(номер позиции) - перемещает указатель на указанную позицию (выставляет указатель перед указанной позицией, как на
  картинках выше).
  Соответственно seek(0) переместит указатель в начало файла, а seek(файл.length()) переместит указатель в конец файла.

- getFilePointer() - возвращает текущую позицию, на которой находится указатель в данный момент.
  Как было указано выше, файл произвольного доступа - это последовательность байтов, поэтому этот и предыдущий методы
  устанавливают и возвращают позицию именно в байтах.
  То есть если у нас, например, в файле записано несколько значений типа int, то чтобы прочитать второе значение, нужно
  ставить указатель на 4 позицию, так как первые 4 байта (0-3 ячейки) будет занимать первое значение типа int.

При создании файла произвольного доступа (объекта RandomAccessFile), помимо локации исходного файла нужно указывать
режим:

```java
RandomAccessFile randomAccess = new RandomAccessFile("data/random.txt", "r");
```

Режимы бывают трех типов: "r" - файл будет открыт только для чтения, "rw" - чтение и запись, "rws" - чтение и запись,
при этом каждое изменение файла мгновенно отражается в исходном файле (то есть изменения сразу же сохраняются на
носителе).
Если указанного файла не существует, то в режиме "r" будет выброшено исключение FileNotFoundException, а в режиме "rw"
и "rws" будет создан новый файл с указанным названием.

```java
import java.io.RandomAccessFile;
import java.io.IOException;

public class RandomAccessFileExample {
    public static void main(String[] args) {
        try (RandomAccessFile raf = new RandomAccessFile("example.dat", "rw")) {
            raf.writeInt(42);         // Записываем целое число
            raf.writeDouble(3.14159); // Записываем число с плавающей точкой
            raf.writeUTF("Привет!");  // Записываем строку в формате UTF-8
        } catch (IOException e) {
            System.out.println("Ошибка при работе с файлом: " + e.getMessage());
        }
    }
}

Запись данных в файл
```

```java
import java.io.RandomAccessFile;
import java.io.IOException;

public class RandomAccessFileReadExample {
    public static void main(String[] args) {
        try (RandomAccessFile raf = new RandomAccessFile("example.dat", "r")) {
            int number = raf.readInt();       // Читаем целое число
            double pi = raf.readDouble();     // Читаем число с плавающей точкой
            String message = raf.readUTF();  // Читаем строку в формате UTF-8

            System.out.println("Число: " + number);
            System.out.println("Число Пи: " + pi);
            System.out.println("Сообщение: " + message);
        } catch (IOException e) {
            System.out.println("Ошибка при чтении файла: " + e.getMessage());
        }
    }
}

Чтение данных из файла
```

```java
import java.io.RandomAccessFile;
import java.io.IOException;

public class RandomAccessFileSeekExample {
    public static void main(String[] args) {
        try (RandomAccessFile raf = new RandomAccessFile("example.dat", "rw")) {
            raf.seek(4); // Перемещаемся на 4-й байт
            raf.writeInt(99); // Перезаписываем данные

            raf.seek(0); // Возвращаемся в начало
            System.out.println("Перезаписанное число: " + raf.readInt());
        } catch (IOException e) {
            System.out.println("Ошибка: " + e.getMessage());
        }
    }
}
```

[К оглавлению](#IO)

# 29. Данные в каком виде можно считывать байтовыми и символьными потоками?

Если нужно работать только с текстовыми (символьными) данными, то рекомендуется использовать символьные потоки и их
обёртки (*Reader / *Writer), а если данные имеют байтовый или смешанный вид, то рекомендуется применять байтовые потоки
и их обёртки (*InputStream / *OuputStream). Это важно не только с точки зрения производительности, но и с точки зрения
целостности данных. Например, нельзя прочитать файл png символьным потоком, так как *.png файл содержит только байтовые
данные, которые невозможно привести к символам.

[К оглавлению](#IO)

# 30. Что такое сокет?

Socket (сокет) – это программный интерфейс, который позволяет программам обмениваться данными через сетевое соединение.
Он предоставляет удобную абстракцию для работы с сетевыми протоколами, такими как TCP/IP или UDP.
С помощью сокетов можно создавать клиент-серверные приложения, где серверный сокет ждет подключения клиентов,
а клиентский сокет устанавливает соединение с сервером.

```java
Пример использования TCP-сокетов

import java.io.*;
import java.net.*;

public class Server {
    public static void main(String[] args) {
        try (ServerSocket serverSocket = new ServerSocket(8080)) {
            System.out.println("Сервер запущен, ожидаем подключения...");

            try (Socket clientSocket = serverSocket.accept(); // Ожидаем клиента
                 BufferedReader in = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()));
                 PrintWriter out = new PrintWriter(clientSocket.getOutputStream(), true)) {

                System.out.println("Клиент подключился!");

                String message;
                while ((message = in.readLine()) != null) {
                    System.out.println("Сообщение от клиента: " + message);
                    out.println("Сервер получил: " + message);
                }
            }
        } catch (IOException e) {
            System.err.println("Ошибка сервера: " + e.getMessage());
        }
    }
}

Сервер
```

```java
import java.io.*;
import java.net.*;

public class Client {
    public static void main(String[] args) {
        try (Socket socket = new Socket("localhost", 8080);
             BufferedReader in = new BufferedReader(new InputStreamReader(socket.getInputStream()));
             PrintWriter out = new PrintWriter(socket.getOutputStream(), true);
             BufferedReader consoleInput = new BufferedReader(new InputStreamReader(System.in))) {

            System.out.println("Подключен к серверу!");

            String userInput;
            while ((userInput = consoleInput.readLine()) != null) {
                out.println(userInput); // Отправляем данные на сервер
                System.out.println("Ответ сервера: " + in.readLine());
            }
        } catch (IOException e) {
            System.err.println("Ошибка клиента: " + e.getMessage());
        }
    }
}

Клиент
```

#### Как это работает?

+ Сервер: Создает объект ServerSocket и ожидает подключения.
  Принимает запрос от клиента с помощью метода accept().
  Создает сокет для взаимодействия с конкретным клиентом.
+ Клиент: Создает объект Socket, чтобы подключиться к серверу (указывая IP-адрес и порт).
  Устанавливает соединение с сервером и обменивается данными через потоки.

[К оглавлению](#IO)

# 31. Какие виды сокетов есть в Java? С каким протоколом они работают?

В Java есть специальный пакет для работы с сетью: java.net.

`java.net.ServerSocket` - класс реализует серверный сокет, который ожидает запросы, приходящие от клиентов по сети, и может отправлять ответ.

`java.net.Socket` - класс реализует клиентский сокет.

Соединение между java - сокетами устанавливается с помощью транспортного протокола TCP.
То есть используя сокеты мы можем передавать и получать информацию по установленному TCP - соединению.

[К оглавлению](#IO)

# 32. Как отправить через сокет сообщение?

1) создаём сервер

```java
try (ServerSocket server = new ServerSocket(portNumber))
```

2) Вызов метода accept() заставляет программу ждать подключений по указанному порту, работа программы продолжится только после подключения клиента.
   После успешного подключения метод возвращает объект Socket, который используется для взаимодействия с клиентом.

```java
Socket socket = server.accept();
```

3) С помощью объекта socket получаем входной поток и отправляем данные в выходной потоки

```java
try (OutputStream out = socket.getOutputStream();
    BufferedReader in = new BufferedReader(
        new InputStreamReader(socket.getInputStream()))) {
```

4) читаем весь входной поток

```java
for (String str = in.readLine(); str != null && !str.isEmpty(); str = in.readLine()) {
   System.out.println(str);
}
```

5) После чтения отправляем ответ окончательно

```java
out.flush();
```

[К оглавлению](#IO)

# 33. Что такое логирование?

Логирование - это процесс записи в файл полезной информации о работе программы.
Полученный файл называют лог-файлом. Если приложение работает плохо, то первое, что проверяют - это лог файл

```java
import java.util.logging.Logger;
import java.util.logging.Level;

public class LoggingExample {
    private static final Logger logger = Logger.getLogger(LoggingExample.class.getName());

    public static void main(String[] args) {
        logger.info("Приложение запущено");
        logger.warning("Это предупреждение");
        logger.severe("Произошла ошибка");
    }
}
```

[К оглавлению](#IO)

# 34. Какие уровни логирования вы знаете?

+ TRACE - предназначен для записи наиболее подробной информации в журнал, например, отслеживания потока выполнения
программы или отладочной информации.
+ DEBUG - используется для записи информации, полезной для отладки программы
+ INFO - используется для записи информации о событиях, которые могут быть полезны для контроля работы программы.
Он может содержать записи о выполненных действиях, основных настройках, успешных завершениях операций и других важных
событиях
+ WARN - используется для записи предупреждений о потенциальных проблемах или событиях, которые могут привести к ошибкам
или нежелательным результатам
+ ERROR - используется для записи критических ошибок, которые приводят к некорректному функционированию программы или
прерывают ее работу
+ FATAL - Записи этого уровня указывают на критические ошибки, при которых невозможно продолжить нормальную работу
программы.
+ OFF - это особый уровень, который позволяет полностью отключить запись логов. Когда установлен уровень логирования OFF,
никакие записи не будут регистрироваться в журнале логов, независимо от их типа или уровня

[К оглавлению](#IO)

# 35. Какая библиотека для логирования используется в курсе? Как ее настроить?

Использовали 2 варианта:

#### Log4j:

1) в pom.xml добавить зависимость
```java
<dependency>
    <groupId>log4j</groupId>
    <artifactId>log4j</artifactId>
    <version>1.2.17</version> // указать актуальную версию
</dependency>
```
2) создать файл /src/main/resources/log4j.properties
   и указать в нём
+   log4j.rootLogger=DEBUG, console //Уровень логирования

+   log4j.appender.console=org.apache.log4j.ConsoleAppender //вывод информации в консоль

+   log4j.appender.console.layout=org.apache.log4j.PatternLayout //формат записи

+   log4j.appender.console.layout.ConversionPattern=%d{ISO8601} %5p %c:%M:%L - %m%n //Дата, Уровень сообщения, Класс, метод, строчка, Текст сообщения

3) импортировать библиотеку

import org.apache.log4j.LogManager;

import org.apache.log4j.Logger;

4) private static final Logger LOG = LogManager.getLogger(ClassName.class.getName());

#### slf4j:

Позволяет абстрагироваться от конкретных библиотек. Это позволяет придерживаться единого стиля логирования для проектов.

1) в pom.xml добавить зависимость
```java
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-log4j12</artifactId>
    <version>1.7.30</version> // указать актуальную версию
</dependency>
```

2) импортировать библиотеку

import org.slf4j.Logger;

import org.slf4j.LoggerFactory;

3)  private static final Logger LOG = LoggerFactory.getLogger(ClassName.class.getName());


[К оглавлению](#IO)

# 36. Опишите из каких элементов состоит формат JSON

Примитивные типы данных:
число (целое или вещественное)
литералы true, false и null
строка — символы юникода, заключённые в двойные кавычки

Ссылочные типы данных:
Объект - заключается в фигурные скобки ({ и }) и содержит разделенный запятой список пар имя/значение.
Массив - заключается в квадратные скобки ([ и ]) и содержит разделенный запятой список значений.
```java
{
        "name":"Alice",
        "age":25,
        "isStudent":false,
        "address":{
        "street":"123 Main St",
        "city":"New York",
        "zipCode":"10001"
        },
        "courses":["Math","Science","History"],
        "graduated":null
        }

Пример более сложной структуры JSON
"name","age","isStudent","graduated" - это ключи, а
их значения —строки,число,булево значение и null соответственно .
"address" — это вложенный объект с другими ключами и значениями.
"courses" — это массив строк .
```

[К оглавлению](#IO)

# 37. Как преобразовать POJO в или из json?

Jackson — это мощная библиотека для работы с JSON в Java. Она предоставляет простой способ преобразования объектов в JSON и обратно.

+ Зависимости для Jackson Для использования Jackson в проекте, необходимо добавить зависимость в файл pom.xml (для Maven) или build.gradle (для Gradle).

Характеристика POJO:
- не наследуется от других классов (возможно, кроме POJO-классов того же пакета)
- не реализует интерфейсов (иногда делается исключение для маркерных интерфейсов из стандартной библиотеки, или тех, которые нужны для бизнес-модели),
- не использует аннотаций в определениях
- не зависит от сторонних библиотек.
```java
Пример POJO-класса

public class Person {
    private String name;
    private int age;

    // Конструкторы, геттеры и сеттеры
    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

+ Преобразование из POJO в JSON (Сериализация)
```java
import com.fasterxml.jackson.databind.ObjectMapper;

public class JacksonExample {
    public static void main(String[] args) {
        try {
            Person person = new Person("Alice", 30);

            // Создание объекта ObjectMapper
            ObjectMapper objectMapper = new ObjectMapper();

            // Преобразование объекта Person в JSON
            String json = objectMapper.writeValueAsString(person);
            System.out.println(json); // Выводит: {"name":"Alice","age":30}
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```
+ Преобразование из JSON в POJO (Десериализация)
```java
import com.fasterxml.jackson.databind.ObjectMapper;

public class JacksonExample {
    public static void main(String[] args) {
        try {
            String json = "{\"name\":\"Alice\",\"age\":30}";

            // Создание объекта ObjectMapper
            ObjectMapper objectMapper = new ObjectMapper();

            // Преобразование JSON в объект Person
            Person person = objectMapper.readValue(json, Person.class);
            System.out.println(person.getName()); // Выводит: Alice
            System.out.println(person.getAge());  // Выводит: 30
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

[К оглавлению](#IO)

# 38. Опишите из каких элементов состоит формат XML

+ Версия xml
+ Кодировка
+ Корневой элемент
+ Вложенные элементы
+ Атрибуты
+ Комментарии 

```java
Пример XML-документа

<? xml version = "1.0"
encoding="UTF-8"?>
<person xmlns="http://example.com/person">
    <name>Alice</name>
    <age>30</age>
    <address>
<street> Main Street 123</street>
<city> New York</city>
    </address>
    <phone type="mobile">123-456-7890</phone>
</person>

<? xml version = "1.0"encoding="UTF-8"?> — декларация XML.
<person> — основной элемент, содержащий имя и возраст.
Внутри элемента <person> находятся другие элементы,
такие как <name>, <age>, <address>, <phone>.
type="mobile" — атрибут в элементе<phone>. 
xmlns="http://example.com/person" — пространство имён 
для предотвращения конфликтов.
```

[К оглавлению](#IO)

# 39. Как преобразовать POJO в или из xml?

Характеристика POJO:
- не наследуется от других классов (возможно, кроме POJO-классов того же пакета)
- не реализует интерфейсов (иногда делается исключение для маркерных интерфейсов из стандартной библиотеки, или тех, которые нужны для бизнес-модели),
- не использует аннотаций в определениях
- не зависит от сторонних библиотек.

Преобразование:
0) добавить конструктор по умолчанию
1) Указать корневой тег через аннотацию @XmlRootElement. Эту аннотацию нужно ставить над сущностью, которая будет корневой
2) Над вложенными сущностями нам нужно поставить просто @XmlElement
3) Для того чтобы поле считалось атрибутом нужно поставить @XmlAttribute, по умолчанию поле парсится как тег

```java
Для начала создадим простой POJO-класс с аннотациями JAXB

import javax.xml.bind.annotation.XmlElement;
import javax.xml.bind.annotation.XmlRootElement;

@XmlRootElement
public class Person {
    private String name;
    private int age;

    // Конструкторы, геттеры и сеттеры
    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @XmlElement
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    @XmlElement
    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

@XmlRootElement указывает, что класс может быть корневым элементом
XML-документа.
@XmlElement указывает, что методы, помеченные этой аннотацией, будут
сериализованы как элементы XML.
```

+ Преобразование из POJO в XML (Сериализация)

```java
Чтобы преобразовать объект в XML,используем JAXBContext и Marshaller

import javax.xml.bind.JAXBContext;
import javax.xml.bind.JAXBException;
import javax.xml.bind.Marshaller;
import java.io.StringWriter;

public class JAXBExample {
    public static void main(String[] args) {
        try {
            Person person = new Person("Alice", 30);

            // Создание контекста JAXB для класса Person
            JAXBContext context = JAXBContext.newInstance(Person.class);

            // Создание объекта Marshaller для преобразования в XML
            Marshaller marshaller = context.createMarshaller();

            // Преобразование в строку XML
            StringWriter writer = new StringWriter();
            marshaller.marshal(person, writer);
            String xml = writer.toString();

            // Выводим XML строку
            System.out.println(xml);
        } catch (JAXBException e) {
            e.printStackTrace();
        }
    }
}

Результат

<? xml version = "1.0"
encoding="UTF-8"standalone="yes"?>
<person>
    <name>Alice</name>
    <age>30</age>
</person>

Мы использовали JAXBContext.

newInstance(),чтобы создать контекст для сериализации.

Метод marshal() преобразует объект в XML.
Мы использовали StringWriter для записи результата в строку.
```

+ Преобразование из XML в POJO (Десериализация)

```java
Для преобразования XML обратно в объект POJO используем Unmarshaller

import javax.xml.bind.JAXBContext;
import javax.xml.bind.JAXBException;
import javax.xml.bind.Unmarshaller;
import java.io.StringReader;

public class JAXBExample {
    public static void main(String[] args) {
        try {
            String xml = "<?xml version=\"1.0\" encoding=\"UTF-8\" standalone=\"yes\"?>"
                    + "<person>"
                    + "<name>Alice</name>"
                    + "<age>30</age>"
                    + "</person>";

            // Создание контекста JAXB для класса Person
            JAXBContext context = JAXBContext.newInstance(Person.class);

            // Создание объекта Unmarshaller для преобразования XML в объект
            Unmarshaller unmarshaller = context.createUnmarshaller();

            // Преобразование XML в объект Person
            StringReader reader = new StringReader(xml);
            Person person = (Person) unmarshaller.unmarshal(reader);

            // Выводим результат
            System.out.println(person.getName());  // Выводит: Alice
            System.out.println(person.getAge());   // Выводит: 30
        } catch (JAXBException e) {
            e.printStackTrace();
        }
    }
}

Результат

Alice
30

Мы использовали Unmarshaller для десериализации.
Метод unmarshal() преобразует XML в объект POJO.
```

[К оглавлению](#IO)

# 40. Что такое сериализация, десериализация?

Сериализация – процесс преобразования объектов в бинарный (т.е. последовательность битов) или текстовый формат.

Десериализация – процесс преобразования сериализованных данных в объекты, т.е. операция обратная сериализации.

Обычно механизм сериализации/десериализации используется для сохранения состояния программы между запусками, хранения настроек, передачи данных между программами локально или по сети.
В Java существует стандартный механизм сериализации в бинарный формат – Java serialization, из текстовых форматов наиболее популярны JSON, XML, YAML, BSON (binary JSON).

Для стандартной сериализации объекта необходимо в классе имплементировать интерфейс Serializable, этот интерфейс является маркерным,
т.е. нет необходимости реализовывать его методы, он сообщает JVM, что объект нашего класса может быть сериализован.
Для сериализации объектов в поток используется метод writeObject, для чтения из потока readObject класса ObjectOutputStream.

Замечания:
- Поле serialVersionUID - уникальный идентификатор версии сериализованного класса, необходим для обеспечения механизмов версионности,
  т.е. нужен JVM для понимания, что сериализованный объект при десериализации имеет те же члены класса, методы и пр.
  Если значения не совпадают, будет выброшено исключение java.io.InvalidClassException.

- При сериализации объекта сериализуются все объекты, на которые он ссылается в своих полях, поэтому вложенные объекты тоже должны быть Serializable

- Для исключения полей из сериализации используется ключевое слово transient

- С помощью интерфейса Externalizable можно реализовать собственный алгоритм сериализации/десериализации,
  для этого нужно переопределить два обязательных метода — writeExternal() и readExternal()


```java
Чтобы объект можно было сериализовать,класс должен реализовывать интерфейс Serializable.

import java.io.*;

class Person implements Serializable {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Геттеры и сеттеры
}

public class SerializationExample {
    public static void main(String[] args) {
        try {
            Person person = new Person("Alice", 30);
            // Создание потока для записи в файл
            FileOutputStream fileOut = new FileOutputStream("person.ser");
            ObjectOutputStream out = new ObjectOutputStream(fileOut);

            // Сериализация объекта
            out.writeObject(person);

            // Закрытие потока
            out.close();
            fileOut.close();

            System.out.println("Object has been serialized");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

Метод writeObject() используется для сериализации объекта.
После сериализации объект сохраняется в файл с расширением .ser или
другом формате для дальнейшего использования .
```

```java
import java.io.*;

class Person implements Serializable {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Геттеры и сеттеры
}

public class DeserializationExample {
    public static void main(String[] args) {
        try {
            // Создание потока для чтения из файла
            FileInputStream fileIn = new FileInputStream("person.ser");
            ObjectInputStream in = new ObjectInputStream(fileIn);

            // Десериализация объекта
            Person person = (Person) in.readObject();

            // Закрытие потока
            in.close();
            fileIn.close();

            // Выводим восстановленный объект
            System.out.println("Name: " + person.name);
            System.out.println("Age: " + person.age);
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}

Метод readObject() используется для десериализации объекта.
После десериализации объект восстанавливается в том виде,
в каком он был до сериализации.
```

#### Примечания:

+ Serializable — интерфейс, который должен реализовать класс, чтобы его объекты могли быть сериализованы.
+ Transient — ключевое слово, которое позволяет исключить поля объекта из процесса сериализации. Если поле помечено как
  transient, оно не будет сериализовано.

[К оглавлению](#IO)

# 41. Что такое регулярные выражения? Зачем они нужны?

Регулярные выражения (Regular Expressions или RegEx) - это шаблоны, с помощью которых производится поиск по совпадению в тексте.
То есть это строка, описывающая последовательность символов, которую желаем найти.
С помощью определенного синтаксиса искать можно не только символы напрямую, но и целые диапазоны или комбинации символов.
Тем самым можно создавать самые разнообразные шаблоны для поиска с помощью последовательности обычных символов, метасимволов и квантификаторов.


```java
Проверка,соответствует ли строка определённому шаблону(например,номеру телефона)

import java.util.regex.*;

public class RegexExample {
    public static void main(String[] args) {
        String phoneNumber = "+1-800-555-1234";

        // Регулярное выражение для поиска номера телефона
        String regex = "^\\+\\d{1,3}-\\d{3}-\\d{3}-\\d{4}$";

        // Создаём шаблон
        Pattern pattern = Pattern.compile(regex);

        // Проверяем, соответствует ли строка шаблону
        Matcher matcher = pattern.matcher(phoneNumber);
        if (matcher.matches()) {
            System.out.println("Номер телефона валиден.");
        } else {
            System.out.println("Номер телефона невалиден.");
        }
    }
}

^ и $ — это границы строки(начало и конец).
\\+ — экранированный символ "+".
\\d {1, 3} —от 1до 3цифр .
\\d {3}-\\d {3}-\\ d {4} — формат номера телефона с тире.
```

```java
Замена всех вхождений слова"яблоко"на"груша"

import java.util.regex.*;

public class RegexExample {
    public static void main(String[] args) {
        String text = "Я люблю яблоки. Я купил яблоко вчера.";

        // Регулярное выражение для поиска слова "яблоко"
        String regex = "яблоко";

        // Заменяем все вхождения слова "яблоко" на "груша"
        String replacedText = text.replaceAll(regex, "груша");

        System.out.println(replacedText);  // "Я люблю груши. Я купил грушу вчера."
    }
}
```

```java
Извлечение всех email-адресов из текста

import java.util.regex.*;
import java.util.*;

public class RegexExample {
    public static void main(String[] args) {
        String text = "Пожалуйста, свяжитесь с нами по адресу support@example.com или admin@domain.com.";

        // Регулярное выражение для поиска email-адресов
        String regex = "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}";

        // Создаём шаблон
        Pattern pattern = Pattern.compile(regex);

        // Создаём матчеры для нахождения всех совпадений
        Matcher matcher = pattern.matcher(text);

        // Собираем все найденные email-адреса
        List<String> emails = new ArrayList<>();
        while (matcher.find()) {
            emails.add(matcher.group());
        }

        System.out.println("Найденные email-адреса: " + emails);
    }
}

Результат

Найденные email-адреса:[support@example.com,admin@domain.com]
```

#### Основные символы и конструкции регулярных выражений

+ `^` и `$` — начало и конец строки.
+ `\\d` — любая цифра (эквивалентно [0-9]).
+ `\\w` — любой символ (буква, цифра или подчёркивание).
+ `\\s` — пробельный символ.
+ `{n,m}` — от n до m повторений.
+ `[]` — класс символов (например, [a-z] означает любую строчную букву).
+ `|` — логическое ИЛИ (например, abc|def соответствует "abc" или "def").
+ `()` — группа (используется для объединения символов в подшаблоны или захвата данных).
+ `.` — любой символ (кроме символа новой строки).
+ `*` — 0 или более повторений предыдущего элемента.
+ `+` — 1 или более повторений предыдущего элемента.
+ `?` — 0 или 1 повторение предыдущего элемента.

[К оглавлению](#IO)

# 42. Как создать регулярное выражение в Java?

В Java работа с регулярными выражениями производится с помощью классов Pattern и Matcher из пакета java.util.regex.
Эти классы работают в паре. В классе Pattern определяется регулярное выражение (создается шаблон и сопоставитель),
а с помощью класса Matcher производится сопоставление шаблона с текстом.

```java
Пример создания регулярного выражения в Java

import java.util.regex.*;

public class RegexExample {
    public static void main(String[] args) {
        // Шаблон для поиска email-адресов
        String regex = "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}";

        // Компиляция регулярного выражения в объект Pattern
        Pattern pattern = Pattern.compile(regex);

        // Пример строки для проверки
        String text = "Мой email: example@mail.com, а еще есть test@domain.org.";

        // Создание Matcher для поиска совпадений в строке
        Matcher matcher = pattern.matcher(text);

        // Поиск всех совпадений и вывод
        while (matcher.find()) {
            System.out.println("Найден email: " + matcher.group());
        }
    }
}

Pattern.compile(regex) — компилирует строк с регулярным выражением в
объект Pattern.
matcher.find() — ищет первое совпадение в строке.
matcher.group() — возвращает совпавшую часть строк
```

```java
игнорировать регистр

Pattern pattern = Pattern.compile("abc", Pattern.CASE_INSENSITIVE);

В этом примере флаг Pattern.CASE_INSENSITIVE делает
регулярное выражение нечувствительным к регистру
(будет найдено и"abc", и "ABC").
```

[К оглавлению](#IO)

# 43. Что такое метасимволы? Для чего они применяются в регулярных выражениях

Метасимволы — это специальные символы в регулярных выражениях, которые имеют особое значение и не соответствуют обычным
символам, а выполняют особые функции для построения шаблонов. Они позволяют задать более сложные правила поиска и
манипуляции текстом.

#### Зачем используются метасимволы?

Метасимволы дают возможность:

+ Описывать шаблоны поиска: Они позволяют указать, какие символы могут быть в строках, например, цифры, буквы, пробелы и
  другие.
+ Управлять повторениями: Метасимволы могут использоваться для указания, сколько раз должен повторяться определённый
  элемент шаблона.
+ Группировка символов: Они позволяют группировать части выражений для последующего использования или ссылки на них.
+ Работа с позициями в строках: Метасимволы могут задавать поиск в начале, в конце строки или внутри строки.

#### Основные метасимволы и их применение

+ `^` — Начало строки Используется для указания, что поиск должен начинаться с начала строки.
  Пример: ^abc — соответствует строкам, начинающимся с "abc".
+ `$` — Конец строки Используется для указания, что поиск должен заканчиваться в конце строки.
  Пример: abc$ — соответствует строкам, заканчивающимся на "abc".
+ `.` — Любой символ (кроме новой строки) Представляет собой любой символ, кроме символа новой строки.
  Пример: a.c — соответствует строкам вроде "abc", "axc", но не "ac" (так как между "a" и "c" должен быть хотя бы один
  символ).
+ `[]` — Квадратные скобки (класс символов) Внутри скобок указываются символы, из которых может быть выбран один.
  Пример: [abc] — соответствует любому из символов "a", "b", или "c".
  Пример: [0-9] — соответствует любой цифре от 0 до 9.
+ `|` — ИЛИ (альтернатива) Позволяет указать альтернативы в шаблоне.
  Пример: abc|def — соответствует строкам, содержащим "abc" или "def".
+ `()` — Группировка (подмаски) Группирует части регулярного выражения для последующего использования или для применения
  к ним квантификаторов.
  Пример: (abc)+ — соответствует одному или нескольким вхождениям "abc".
+ `*` — Ноль или более повторений Соответствует нулю или более повторениям предыдущего символа или группы.
  Пример: a*b — соответствует "b", "ab", "aab", "aaab" и так далее.
+ `+` — Один или более повторений Соответствует одному или более повторениям предыдущего символа или группы.
  Пример: a+b — соответствует "ab", "aab", "aaab" и так далее, но не "b".
+ `?` — Ноль или одно повторение Соответствует нулю или одному повторению предыдущего символа или группы.
  Пример: a?b — соответствует "b" или "ab".
+ `{n,m}` — От n до m повторений Указывает на количество повторений, которое должно быть между n и m.
  Пример: a{2,4} — соответствует строкам "aa", "aaa" или "aaaa".
+ `\d` — Цифры Соответствует любой цифре, эквивалентно [0-9].
  Пример: \d+ — соответствует одному или более числовым символам.
+ `\w` — Буквы, цифры или подчеркивания Соответствует любому символу из набора "a-z", "A-Z", "0-9" или "_".
  Пример: \w+ — соответствует последовательности букв, цифр или подчеркиваний.
+ `\s` — Пробельные символы Соответствует любому пробельному символу, включая пробелы, табуляции и символы новой строки.
  Пример: \s+ — соответствует одному или более пробельным символам.
+ `\b` — Граница слова Соответствует границе слова (между буквой и не-буковым символом).
  Пример: \bword\b — соответствует только целому слову "word", а не "sword" или "wordy".
+ `\` — Экранирование Используется для экранирования метасимволов или для обозначения специальных символов.
  Пример: \\ — соответствует символу обратной косой черты.

```java
Использование метасимволов для проверки email-адреса

import java.util.regex.*;

public class RegexExample {
    public static void main(String[] args) {
        String emailRegex = "^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$";
        String email = "example@mail.com";

        Pattern pattern = Pattern.compile(emailRegex);
        Matcher matcher = pattern.matcher(email);

        if (matcher.matches()) {
            System.out.println("Это валидный email.");
        } else {
            System.out.println("Это невалидный email.");
        }
    }
}

^ — начало строки. 
[a-zA-Z0-9._%+-]+ — одна или более букв, цифр, точек, подчёркиваний, процентов и других  символов .
@ —символ "@".
[a-zA-Z0-9.-]+ — одна или более букв, цифр, точек или дефисов.
\\. — символ точки(необходимо экранировать).
[a-zA-Z]{2,} — две или более букв(для домена верхнего уровня, например, ".com").
$ —  конец строки.
```

Метасимволы разделены на несколько групп:

1) Поиск символов или слов: например, символ "." (точка) соответствует любому одиночному символу, а символы "\w" и "\b" используются для поиска слов.
2) Квантификаторы: например, символы "*" (ноль или более повторений), "+" (одно или более повторений) и "?" (ноль или одно повторение) применяются для указания количества повторений символов.
3) Классы символов: например, символы "\d" (цифры), "\s" (пробелы) и "\w" (буквы, цифры и символ подчеркивания) представляют определенные классы символов.
4) Альтернация: символ "|" (вертикальная черта) используется для указания альтернативных вариантов поиска.
5) Захват групп: символы "(" и ")" используются для создания группировки и захвата определенного фрагмента.

Квантификаторы имеют несколько режимов: жадный, сверхжадный и ленивый.

1) жадный:
   Все квантификаторы по умолчанию работают в жадном режиме. Его работа заключается в том, что всегда ищется максимально длинное совпадение.

2) сверхжадный:
   Добавляется символ "+", можно использовать когда точно знаем что ищем, и оставшуюся часть можно отбросить

3) ленивый:
   Записывается в виде символа "?" после квантификатора. Ленивый режим ищет самую короткую последовательность.


[К оглавлению](#IO)