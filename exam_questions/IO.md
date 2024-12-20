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

Поток ввода-вывода - это абстракция для потребления или поставки данных. Цель создания InputStream и OutputStream это
абстрактный доступ к вводу и выводу. Источник при этом не важен. Это может быть файл, консоль, веб-страница. Stream -
это бесконечный поток данных, подключенный к источнику данных

[К оглавлению](#IO)

# 2. Что такое Java IO?

IO API - абстрактный доступ к вводу-выводу, чтобы не зависеть от подробностей реализации физических устройств.

Поток ввода - это объект, из которого можно считать данные (input) - чтение.

Поток вывода - это объект, в который можно записать данные (output) - запись.

Java IO подразделяется на две основные категории: байтовый (byte-oriented) и символьный (character-oriented) ввод-вывод.

Байтовый ввод-вывод (`java.io`) работает с данными в виде байтов.
Он обеспечивает потоки байтового ввода (`InputStream`) и байтового вывода (`OutputStream`),
которые могут использоваться для чтения и записи данных из и в различные источники, такие как файлы,
сетевые соединения и другие. Байтовые потоки часто используются для работы с необработанными двоичными данными.

Символьный ввод-вывод (`java.io`) работает с данными в виде символов, используя стандартные наборы символов, такие как
Unicode.
Он предоставляет символьные потоки ввода (`Reader`) и вывода (`Writer`), которые могут использоваться для чтения и
записи текстовых данных из и в различные источники.
Символьные потоки обеспечивают более высокоуровневые операции, такие как чтение и запись строк или работу с символами
вместо байтов.


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

**Классы Java IO API**

**Базовые**

+ `InputStream` /` OutputStream` - абстрактный класс, определяющий потоковый байтовый ввод/вывод
+ `Reader` / `Writer` - Символьные потоки имеют два основных абстрактных класса `Reader` и `Writer`,
  управляющие потоками символов `Unicode`.
+ `InputStreamReader` / `OutputStreamWriter` Входной/выводной поток, транслирующий байты в символы

**Массивы**

+ `ByteArrayInputStream` / `ByteArrayOutputStream` - использует байтовый массив в потоке.
+ `CharArrayReader` / `CharArrayWriter` - читает/пишет из символьного массива.

**Files**

+ `FileInputStream` / `FileOutputStream` - Чтение/Отправка данных в файл на диске. Реализация класса `OutputStream`
+ `RandomAccessFile` / `RandomAccessFile` - Чтение/запись файлов с произвольным доступом. метод `seek()` позволяет
  переместиться к определенной позиции и изменить хранящееся там значение.
  При использовании RandomAccessFile необходимо знать структуру файла. Класс `RandomAccessFile` содержит методы для
  чтения
  и записи примитивов и строк UTF-8.
  `RandomAccessFile` может открываться в режиме чтения ("r") или чтения/записи ("rw"). Также есть режим "rws", когда
  файл
  открывается для операций чтения-записи и каждое изменение данных файла немедленно записывается на физическое
  устройство.
+ `FileReader` / `FileWriter` `FileWriter` записывает данные в файл. При вводе/выводе практически всегда применяется
  буферизация, поэтому используется `BufferedWriter`.                           
  Когда данные входного потока исчерпываются, метод `readLine()` возвращает `null`. Для потока явно вызывается
  метод `close()`;
  если не вызвать его для всех выходных файловых потоков, в буферах могут остаться данные, и файл получится неполным

**Буферизация**

+ `BufferedInputStream` / `BufferedOutputStream` - буферизируемый поток. Буферы вывода нужно для повышения
  производительности
+ `BufferedReader` / `BufferedWriter`

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

[К оглавлению](#IO)

# 5. Что такое Scanner?

В Java класс `Scanner` представляет собой удобный инструмент для чтения данных.

[К оглавлению](#IO)

# 6. Как работает Scanner внутри?

В качестве источника данных Scanner принимает любой вид данных, включая Reader, InputStream, File для java.io и Readable, Path для java.util.nio.
Также можно задать источник в виде строки String.

Работает как итератор.

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

Классы PrintStream и PrintWriter в Java предназначены для упрощения записи текстовых данных в выходной поток. Они
предоставляют удобные методы для форматирования и записи строк, чисел и других типов данных. Однако у них есть важные
различия в реализации и использовании.

1. Что такое PrintStream? Класс PrintStream используется для записи данных в текстовом формате в поток вывода, например,
   в консоль или файл. Он чаще всего применяется для работы с байтовыми потоками, так как наследуется от класса
   OutputStream.

#### Ключевые особенности PrintStream:

+ Позволяет записывать данные (строки, числа, символы) в поток в удобной форме.
+ Не выбрасывает исключения IOException при записи (ошибки игнорируются).
+ Поддерживает метод print() и его перегруженные варианты.
+ По умолчанию используется для системного вывода через System.out.

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

2. Что такое PrintWriter? Класс PrintWriter аналогичен PrintStream, но предназначен для работы с символьными потоками.
   Это делает его более подходящим для работы с текстовыми файлами или потоками, поддерживающими символы (например,
   Writer).

#### Ключевые особенности PrintWriter:

+ Работает с Writer, а не с OutputStream.
+ Поддерживает буферизацию, что делает его эффективнее для записи текста.
+ Исключения IOException также игнорируются, как и у PrintStream.
+ Подходит для записи текстовых данных, особенно при работе с символами Unicode.

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

#### Когда использовать какой класс?

- PrintStream:
  Для системного вывода (например, System.out).
  Для записи данных в байтовые потоки (например, в файл в бинарном формате).
  Когда требуется простой и быстрый способ записи текста в поток вывода.

+ PrintWriter:
  Для работы с текстовыми файлами или потоками символов.
  Когда важна поддержка Unicode.
  Для форматированной записи текста, особенно если данные хранятся в символах (например, JSON или XML).

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

Потоки байтовых массивов в Java — это потоки ввода/вывода, которые работают с массивами байтов в памяти вместо файлов
или других внешних ресурсов. Они предоставляют удобный способ читать и записывать данные в массивы байтов.

1. ByteArrayInputStream: чтение байтов из массива

#### Как работает?

+ Данные хранятся в массиве байтов, который вы передаете в конструктор.
+ Класс предоставляет методы для последовательного чтения данных из массива.
+ Чтение происходит как будто из файла или другого потока, но источник данных — это массив в памяти.

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

2. ByteArrayOutputStream: запись байтов в массив

#### Как работает?

+ Класс записывает байты в массив, который создается динамически в памяти.
+ Размер массива автоматически увеличивается при записи новых данных.
+ После завершения записи данные можно извлечь в виде массива или строки.

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

#### Когда использовать потоки байтовых массивов?

+ Буферизация данных: Когда нужно временно сохранить данные в памяти для последующей обработки.
+ Тестирование: Легко заменить файл или сеть массивом байтов для имитации ввода/вывода.
+ Обработка данных в памяти: Удобно работать с данными, которые не нужно записывать на диск.
+ Сериализация/Десериализация: Часто используется для работы с объектами или данных в бинарном формате.

[К оглавлению](#IO)

# 28. Зачем нужен класс RandomAccessFile?

Класс RandomAccessFile в Java предназначен для работы с файлами, которые нужно читать или записывать в произвольном
порядке, а не последовательно. Это мощный инструмент для работы с файлами, когда требуется прямой доступ к их
содержимому, без необходимости считывать или записывать данные с начала до конца.

#### Основные возможности RandomAccessFile

+ Произвольный доступ к данным: Можно читать или записывать данные в любом месте файла, управляя позицией указателя
  чтения/записи.
  Указатель текущей позиции изменяется методами для перемещения (seek) и чтения/записи.
+ Режимы работы:r: только чтение. rw: чтение и запись.
+ Поддержка различных типов данных: Методы для чтения и записи примитивных типов (например, readInt, writeDouble).
+ Изменение существующего файла: Можно перезаписывать часть данных файла, не затрагивая остальную его часть.

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

#### Произвольное чтение и запись

Перемещение указателя:
Метод seek(long position) перемещает указатель чтения/записи в указанную позицию.
Например, чтобы записать данные в середине файла или переписать их.

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

#### Реализация RandomAccessFile

Основан на низкоуровневых операциях ввода/вывода (через классы FileDescriptor и нативные методы).
Управляет указателем позиции, который отслеживает, откуда будет происходить следующая операция чтения или записи.
Обеспечивает синхронизацию для потокобезопасного доступа.

#### Когда использовать RandomAccessFile?

+ Редактирование больших файлов:Если файл слишком велик, чтобы загружать его в память, но нужно изменить только часть
  данных.
+ Работа с бинарными форматами данных:Например, с файлами баз данных, мультимедийными файлами или сериализованными
  объектами.
+ Чтение файла по частям:Например, для реализации загрузки или обработки больших данных с учетом их структуры.
+ Тестирование и отладка:Легко проверить содержимое файла или записать данные для экспериментов.

#### Ограничения

+ Только файловая работа: Класс не может использоваться с сетевыми потоками или другими источниками.
+ Неудобство при работе с текстовыми файлами: Требуется самостоятельно обрабатывать преобразование строк в байты и
  обратно.
+ Неавтоматическое расширение файлов: Если указатель перемещается за конец файла, то пустое пространство не заполняется
  автоматически.

[К оглавлению](#IO)

# 29. Данные в каком виде можно считывать байтовыми и символьными потоками?

`1. Байтовые потоки (InputStream и OutputStream)`

#### Что можно считывать?

Байтовые потоки работают с сырыми байтами (8 бит), поэтому они идеально подходят для работы с любыми бинарными данными,
такими как:

+ Файлы: Изображения, аудио, видео.
  Архивы, исполняемые файлы.
+ Протоколы передачи данных:
  Сетевые данные.
  Последовательные порты.
+ Любые двоичные данные:
  Форматы данных, например PDF, DOCX.
  Объекты в сериализованном виде.

```java
import java.io.FileInputStream;
import java.io.IOException;

public class ByteStreamExample {
    public static void main(String[] args) {
        try (FileInputStream fis = new FileInputStream("binary.dat")) {
            int byteData;
            while ((byteData = fis.read()) != -1) {
                System.out.print(byteData + " "); // Читаем байт за байтом
            }
        } catch (IOException e) {
            System.out.println("Ошибка чтения файла: " + e.getMessage());
        }
    }
}

Пример: чтение бинарного файла
```

`2. Символьные потоки (Reader и Writer)`

#### Что можно считывать?

Символьные потоки работают с текстовыми данными (16 бит), которые представлены в виде символов Unicode. Они используются
для чтения и записи текстовых файлов и строк. Примеры:

+ Текстовые файлы: .txt, .csv, .json, .xml.
+ Текст в кодировках: UTF-8, UTF-16, ASCII, и другие.
+ Лог-файлы, конфигурации.

```java
import java.io.FileReader;
import java.io.IOException;

public class CharStreamExample {
    public static void main(String[] args) {
        try (FileReader reader = new FileReader("text.txt")) {
            int charData;
            while ((charData = reader.read()) != -1) {
                System.out.print((char) charData); // Читаем символ за символом
            }
        } catch (IOException e) {
            System.out.println("Ошибка чтения файла: " + e.getMessage());
        }
    }
}

Пример: чтение текстового файла
```

| Характеристика      | Байтовые потоки                              | Символьные потоки                                   |
|---------------------|----------------------------------------------|-----------------------------------------------------|
| Тип данных          | Сырые байты (byte, 8 бит).                   | Символы (char, 16 бит).                             |
| Использование       | Бинарные данные: изображения, видео, архивы. | Текстовые данные: строки, текстовые файлы.          |
| Поддержка кодировок | Кодировка не учитывается                     | Автоматическая поддержка кодировок, например UTF-8. |
| Примеры классов     | FileInputStream, ByteArrayInputStream.       | FileReader, BufferedReader, PrintWriter.            |

#### Особенности выбора подходящего потока

+ Когда использовать байтовые потоки: Если файл содержит не только текст, но и форматированные данные (например, .pdf,
  .jpg, .zip).
  Когда необходимо считывать сырые данные без преобразования.
+ Когда использовать символьные потоки: Если требуется работа с текстовыми файлами.
  Когда нужно обрабатывать строки или символы, особенно с учетом кодировок.
+ Преобразование между потоками: Если данные хранятся в байтовом формате, но нужно их интерпретировать как текст,
  используют классы InputStreamReader или OutputStreamWriter, которые преобразуют байты в символы на основе заданной
  кодировки.

```java
import java.io.FileInputStream;
import java.io.InputStreamReader;
import java.io.BufferedReader;
import java.io.IOException;

public class StreamConversionExample {
    public static void main(String[] args) {
        try (FileInputStream fis = new FileInputStream("text.txt");
             InputStreamReader isr = new InputStreamReader(fis, "UTF-8");
             BufferedReader reader = new BufferedReader(isr)) {

            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            System.out.println("Ошибка чтения файла: " + e.getMessage());
        }
    }
}

Пример преобразования байтового потока в символьный
```

[К оглавлению](#IO)

# 30. Что такое сокет?

Сокет в Java (и в сетевых технологиях в целом) — это программный интерфейс для обмена данными между двумя узлами (
клиентом и сервером) в сети. Он предоставляет средства для создания и управления подключением по сети, отправки и
получения данных.

#### Основные характеристики сокета

+ Сетевой интерфейс: Используется для обмена данными через TCP или UDP протоколы.
  Поддерживает двустороннюю связь (клиент ↔ сервер).
+ Типы сокетов: TCP-сокеты:
  Основаны на протоколе TCP (Transmission Control Protocol).
  Обеспечивают надежную передачу данных с подтверждением доставки.
  Используют классы Socket и ServerSocket в Java.
+ UDP-сокеты: Основаны на протоколе UDP (User Datagram Protocol).
  Менее надежны, но быстрее, так как не требуют подтверждения.
  Используют класс DatagramSocket в Java.
+ Основные операции:Создание сокета.
  Подключение к удаленному узлу.
  Отправка и получение данных.
  Закрытие подключения.

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

```java
Пример использования UDP-сокетов

import java.net.*;

public class UDPServer {
    public static void main(String[] args) {
        try (DatagramSocket socket = new DatagramSocket(8080)) {
            byte[] buffer = new byte[1024];
            DatagramPacket packet = new DatagramPacket(buffer, buffer.length);

            System.out.println("UDP-сервер запущен. Ожидаем данных...");

            socket.receive(packet); // Принимаем данные
            String received = new String(packet.getData(), 0, packet.getLength());
            System.out.println("Получено: " + received);
        } catch (Exception e) {
            System.err.println("Ошибка UDP-сервера: " + e.getMessage());
        }
    }
}

Сервер
```

```java
import java.net.*;

public class UDPClient {
    public static void main(String[] args) {
        try (DatagramSocket socket = new DatagramSocket()) {
            String message = "Привет, сервер!";
            byte[] buffer = message.getBytes();
            InetAddress address = InetAddress.getByName("localhost");

            DatagramPacket packet = new DatagramPacket(buffer, buffer.length, address, 8080);
            socket.send(packet); // Отправляем данные
        } catch (Exception e) {
            System.err.println("Ошибка UDP-клиента: " + e.getMessage());
        }
    }
}

Клиент
```

#### Где используются сокеты?

+ Веб-приложения: HTTP, WebSocket-соединения для общения между клиентом и сервером.
+ Мессенджеры: Передача сообщений в реальном времени.
+ Игры: Организация сетевых матчей.
+ Сетевые службы: Сервисы, работающие по TCP/UDP.

[К оглавлению](#IO)

# 31. Какие виды сокетов есть в Java? С каким протоколом они работают?

1. `TCP-сокеты` Работают с протоколом TCP (Transmission Control Protocol). Этот протокол обеспечивает надежное
   соединение и гарантированную доставку данных.

#### Классы для работы с TCP-сокетами:

+ Socket: клиентский сокет. Используется для установления соединения с сервером.
  Поддерживает двустороннюю передачу данных (чтение/запись через потоки).
+ ServerSocket: серверный сокет. Ожидает входящих подключений от клиентов.
  Создает объекты Socket для каждого подключившегося клиента.

#### Особенности TCP-сокетов:

+ Перед началом передачи данных устанавливается соединение между клиентом и сервером.
+ Данные передаются в виде потока байтов.
+ Контролируется порядок доставки данных и целостность информации.
  Пример использования TCP-сокетов:
  (Код клиента и сервера можно найти в предыдущем ответе.)

2. `UDP-сокеты` Работают с протоколом UDP (User Datagram Protocol). Этот протокол является менее надежным, но более
   быстрым, так как не требует установления соединения.

#### Классы для работы с UDP-сокетами:

+ DatagramSocket: Используется для отправки и получения датаграмм (пакетов данных).
  Работает как на стороне клиента, так и на стороне сервера.
+ DatagramPacket: Представляет собой пакет данных, который можно отправить или получить через DatagramSocket.

#### Особенности UDP-сокетов:

+ Нет установления соединения: сообщения отправляются как независимые пакеты.
+ Нет гарантии доставки, порядка или целостности данных.
+ Подходит для приложений, где важна скорость (например, видеостриминг, онлайн-игры).
  Пример использования UDP-сокетов:
  (Код клиента и сервера приведен в предыдущем ответе.)

| Характеристика     | TCP-сокеты                                  | UDP-сокеты                         |
|--------------------|---------------------------------------------|------------------------------------|
| Протокол	          | TCP (надежный, соединение-ориентированный). | UDP (ненадежный, без соединения).  |
| Гарантия доставки  | Да                                          | Нет                                |
| Порядок доставки   | Гарантирован                                | Не гарантирован                    |
| Производительность | Медленнее из-за накладных расходов.         | Быстрее за счет меньшего контроля. |
| Тип передачи       | Поток данных                                | Отдельные пакеты                   |
| Применение         | Веб-приложения, файловые трансферы.         | Онлайн-игры, потоковое видео.      |

#### Дополнительные виды сокетов:

+ Многоадресные сокеты (Multicast Sockets): Используются для работы с группами узлов в сети.
  Работают на основе UDP.
  Класс: MulticastSocket.
+ Unix Domain Sockets (доступны через библиотеки): Локальные соединения между процессами на одной машине.
  Не являются частью стандартной Java, но могут быть реализованы через сторонние библиотеки.

[К оглавлению](#IO)

# 32. Как отправить через сокет сообщение?

Чтобы отправить сообщение через сокет, в Java используются входные и выходные потоки (InputStream и OutputStream),
которые ассоциированы с сокетом.

#### Пример передачи сообщения через сокет (TCP)

Клиент отправляет сообщение серверу

+ Клиентская сторона: Подключается к серверу с помощью Socket.
  Получает OutputStream из сокета.
  Использует потоки для записи данных (например, PrintWriter или BufferedWriter).
+ Серверная сторона: Принимает соединение через ServerSocket.
  Получает InputStream из клиентского сокета.
  Читает данные через поток (например, BufferedReader или Scanner).

```java
Код клиента

import java.io.*;
import java.net.*;

public class Client {
    public static void main(String[] args) {
        try (Socket socket = new Socket("localhost", 8080); // Подключение к серверу
             PrintWriter out = new PrintWriter(socket.getOutputStream(), true)) { // Поток для отправки данных

            System.out.println("Клиент подключен к серверу.");
            String message = "Привет, сервер!";
            out.println(message); // Отправляем сообщение
            System.out.println("Сообщение отправлено: " + message);

        } catch (IOException e) {
            System.err.println("Ошибка клиента: " + e.getMessage());
        }
    }
}

Код сервера

import java.io .*;
        import java.net .*;

public class Server {
    public static void main(String[] args) {
        try (ServerSocket serverSocket = new ServerSocket(8080)) {
            System.out.println("Сервер запущен и ожидает подключения...");

            try (Socket clientSocket = serverSocket.accept(); // Принимаем подключение клиента
                 BufferedReader in = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()))) { // Поток для чтения данных

                System.out.println("Клиент подключился.");
                String receivedMessage = in.readLine(); // Читаем сообщение
                System.out.println("Сообщение от клиента: " + receivedMessage);
            }

        } catch (IOException e) {
            System.err.println("Ошибка сервера: " + e.getMessage());
        }
    }
}

```

```java
Если клиент и сервер должны обмениваться данными, оба должны использовать и
входной(InputStream),и выходной (OutputStream) потоки.

Код клиента(двусторонний):

        try(
Socket socket = new Socket("localhost", 8080);
PrintWriter out = new PrintWriter(socket.getOutputStream(), true);
BufferedReader in = new BufferedReader(new InputStreamReader(socket.getInputStream()))){

        out.println("Привет, сервер!"); // Отправляем сообщение

String serverResponse = in.readLine(); // Читаем ответ от сервера
    System.out.println("Ответ от сервера: "+serverResponse);

}catch(
IOException e){
        e.printStackTrace();
}

        
Код сервера(двусторонний):

        try(
ServerSocket serverSocket = new ServerSocket(8080)){
        System.out.println("Сервер запущен...");
    
    try(
Socket clientSocket = serverSocket.accept();
BufferedReader in = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()));
PrintWriter out = new PrintWriter(clientSocket.getOutputStream(), true)){

String clientMessage = in.readLine(); // Читаем сообщение от клиента
        System.out.println("Сообщение от клиента: "+clientMessage);
        
        out.println("Сообщение принято!"); // Отправляем ответ клиенту
    }
  }catch(
IOException e){
        e.printStackTrace();
}
```

```java
Если вы используете DatagramSocket(UDP),данные передаются через пакеты.

Код клиента(UDP):

        try(
DatagramSocket socket = new DatagramSocket()){
String message = "Привет, сервер!";
byte[] buffer = message.getBytes();
InetAddress address = InetAddress.getByName("localhost");
DatagramPacket packet = new DatagramPacket(buffer, buffer.length, address, 8080);

    socket.send(packet); // Отправляем пакет
    System.out.println("Пакет отправлен!");
}catch(
IOException e){
        e.printStackTrace();
}

        
Код сервера(UDP):

        try(
DatagramSocket socket = new DatagramSocket(8080)){
byte[] buffer = new byte[1024];
DatagramPacket packet = new DatagramPacket(buffer, buffer.length);

    System.out.println("UDP-сервер запущен...");
    socket.receive(packet); // Получаем пакет

String received = new String(packet.getData(), 0, packet.getLength());
    System.out.println("Сообщение: "+received);
}catch(
IOException e){
        e.printStackTrace();
}


```

[К оглавлению](#IO)

# 33. Что такое логирование?

Логирование — это процесс записи информации о работе программы, который помогает отслеживать её поведение, отлаживать
ошибки и анализировать производительность. Логи (записи) создаются для фиксирования различных событий, состояний, ошибок
или предупреждений в приложении.

#### Зачем нужно логирование?

+ Отладка и диагностика: Помогает разработчикам обнаруживать и исправлять ошибки.
  Удобно для анализа неожиданных ситуаций или багов.
+ Мониторинг: Используется для наблюдения за работой приложения в реальном времени (например, отслеживание активности
  пользователей или загрузки системы).
+ Аудит: Фиксирует действия пользователя и системы для проверки и анализа (например, кто и когда изменил данные).
+ Отчётность и аналитика: Логи могут быть источником данных для отчётов и анализа производительности приложения.

#### Как логирование работает в Java?

1. Стандартное логирование (java.util.logging) Java предоставляет встроенный API для логирования, который поддерживает
   следующие функции:

+ Различные уровни логов.
+ Запись логов в консоль или файл.
+ Настройка через конфигурационные файлы.

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

2. Популярные сторонние библиотеки

+ SLF4J (Simple Logging Facade for Java): Универсальный интерфейс, поддерживающий различные реализации логеров (Logback,
  Log4j и другие).
+ Log4j (Apache): Высокофункциональная библиотека для логирования.
  Поддерживает гибкую конфигурацию через XML, YAML или properties-файлы.
+ Logback: Современная замена Log4j.
  Высокая производительность, поддержка сложных шаблонов и ротации файлов.

```java
import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;

public class Log4jExample {
    private static final Logger logger = LogManager.getLogger(Log4jExample.class);

    public static void main(String[] args) {
        logger.info("Это сообщение уровня INFO");
        logger.error("Это сообщение уровня ERROR");
    }
}

Пример с использованием Log4j
```

#### Где хранятся логи?

+ Консоль: Для удобства просмотра в процессе работы.
+ Файлы: Для долговременного хранения и анализа.
+ Системы мониторинга: Специальные сервисы, такие как ELK Stack, Splunk или Graylog, для централизованного сбора и
  анализа логов.

#### Рекомендации для логирования

+ Используйте подходящий уровень для каждой записи. Не пишите всё в INFO или ERROR.
+ Не включайте в логи конфиденциальную информацию (пароли, токены и т.д.).
+ Логи должны быть читаемыми и содержательными: включайте метки времени, уровни и контекст.
+ Настройте ротацию файлов логов (чтобы они не занимали много места).
+ Логируйте только то, что действительно нужно, чтобы не нагружать систему.

[К оглавлению](#IO)

# 34. Какие уровни логирования вы знаете?

+ TRACE: Самый детальный уровень.
  Используется для отслеживания потока выполнения программы.
+ DEBUG: Предназначен для отладки.
  Показывает техническую информацию, полезную для разработчиков.
+ INFO: Для информации о нормальном ходе выполнения программы.
  Например, "Сервер запущен на порту 8080".
+ WARN: Предупреждения о возможных проблемах.
  Например, "Низкий уровень памяти".
+ ERROR: Сообщения об ошибках, из-за которых программа может частично перестать работать.
  Например, "Не удалось подключиться к базе данных".
+ FATAL: Критические ошибки, приводящие к остановке приложения.

#### Связь уровней логирования и их использования

+ TRACE и DEBUG: Используются в процессе разработки и отладки. На продакшене обычно отключаются.
+ INFO, WARN, ERROR: Используются для мониторинга приложения в продакшене.
+ FATAL: Редко используется, но помогает фиксировать катастрофические сбои.

[К оглавлению](#IO)

# 35. Какая библиотека для логирования используется в курсе? Как ее настроить?

Log4j - библиотека позволяет осуществить логирование процессов в приложении.

Библиотека slf4j позволяет абстрагироваться от конкретных библиотек. Это позволяет придерживаться единого стиля
логгирования для проектов.

[К оглавлению](#IO)

# 36. Опишите из каких элементов состоит формат JSON

JSON (JavaScript Object Notation) — это легковесный формат обмена данными, который используется для представления
структурированных данных в текстовом виде. Он основан на синтаксисе объектов JavaScript, но является независимым от
языка и используется во многих современных приложениях и сервисах для обмена данными, например, в REST API.

#### Основные элементы формата JSON:

1. Объекты (Objects)
   Объект в JSON заключается в фигурные скобки {}.
   Он состоит из набора пар "ключ: значение".
   Ключ всегда является строкой (строчные символы в кавычках "key"), а значение может быть различного типа (строка,
   число, массив, другой объект и т.д.).
   Каждая пара "ключ: значение" разделяется запятой

```java
{
        "name":"Alice",
        "age":25,
        "city":"New York"
        }
```

2. Массивы (Arrays)
   Массив в JSON заключается в квадратные скобки [].
   Он содержит упорядоченный список значений, которые могут быть любого типа (строки, числа, объекты, массивы и т.д.).
   Элементы массива разделяются запятой

```java
["apple","banana","cherry"]
```

3. Строки (Strings)
   Строки в JSON заключаются в двойные кавычки ".
   Они могут содержать любые символы, включая пробелы, буквы и цифры, а также специальные символы (например, \n для
   новой строки).

```java
"Hello, world!"

```

4. Числа (Numbers)
   Числа в JSON могут быть целыми или с плавающей запятой (десятичными числами).
   Они не заключаются в кавычки.

```java
42
        3.1415
```

5. Булевы значения (Booleans)
   JSON поддерживает два булевых значения: true и false
6. `null`
   В JSON также существует специальное значение null, которое используется для представления отсутствующих или
   неопределённых данных

#### Структура JSON:

+ Объект может содержать другие объекты, массивы или примитивные значения.
+ Массив может содержать объекты, другие массивы, строки, числа и т.д.
+ Примитивы (строки, числа, булевы значения и null) могут быть значениями в объектах и массивах.

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

Для преобразования POJO в JSON и наоборот можно использовать Jackson или Gson. Оба варианта широко распространены, и
выбор зависит от требований к производительности и функционалу проекта. Jackson часто используется в крупных и сложных
приложениях, а Gson — в простых и средних по объему проектах.

#### Использование Jackson

Jackson — это мощная библиотека для работы с JSON в Java. Она предоставляет простой способ преобразования объектов в
JSON и обратно.

1. Зависимости для Jackson
   Для использования Jackson в проекте, необходимо добавить зависимость в файл pom.xml (для Maven) или build.gradle (для
   Gradle).
2. Пример POJO-класса

```java
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

3. Преобразование из POJO в JSON (Сериализация)

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

4. Преобразование из JSON в POJO (Десериализация)

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

#### Использование Gson

Gson — это библиотека от Google для работы с JSON. Она также позволяет легко преобразовывать объекты в JSON и наоборот.

1. Зависимости для Gson
2.
    2. Пример POJO-класса. Используем тот же класс Person для примера.
3. Преобразование из POJO в JSON (Сериализация)

```java
import com.google.gson.Gson;

public class GsonExample {
    public static void main(String[] args) {
        Person person = new Person("Bob", 25);

        // Создание объекта Gson
        Gson gson = new Gson();

        // Преобразование объекта Person в JSON
        String json = gson.toJson(person);
        System.out.println(json); // Выводит: {"name":"Bob","age":25}
    }
}
```

4. Преобразование из JSON в POJO (Десериализация)

```java
import com.google.gson.Gson;

public class GsonExample {
    public static void main(String[] args) {
        String json = "{\"name\":\"Bob\",\"age\":25}";

        // Создание объекта Gson
        Gson gson = new Gson();

        // Преобразование JSON в объект Person
        Person person = gson.fromJson(json, Person.class);
        System.out.println(person.getName()); // Выводит: Bob
        System.out.println(person.getAge());  // Выводит: 25
    }
}
```

#### Сравнение Jackson и Gson

+ Jackson: Быстрее, чем Gson, особенно при больших объёмах данных.
  Имеет более широкий функционал и гибкость (например, возможность работы с аннотациями и специфическими форматами).
  Поддерживает более сложные структуры (например, дерево JSON и потоковое чтение/запись).
+ Gson: Легковесная и простая в использовании.
  Может быть предпочтительнее для небольших проектов или случаев, когда не требуется высокая производительность.
  Очень хорошо интегрируется с Android-приложениями.

[К оглавлению](#IO)

# 38. Опишите из каких элементов состоит формат XML

XML (eXtensible Markup Language) — это язык разметки, предназначенный для хранения и передачи данных. В отличие от HTML,
XML не имеет фиксированных тегов; это расширяемый формат, что позволяет пользователю создавать собственные теги в
зависимости от потребностей.

#### Элементы формата XML

1. Объявление XML (XML Declaration) Это опциональная строка, которая указывает, что документ является XML, а также может
   содержать информацию о версии XML и кодировке.
   Обычно появляется в первой строке XML-документа.
2. Элементы (Elements) Основная структура XML-документа. Элементы заключены в теги.
   Элемент состоит из открывающего и закрывающего тега.
   Элемент может содержать атрибуты и текстовое содержимое, а также другие вложенные элементы.

```java
<person>
    <name>Alice</name>
    <age>30</age>
</person>

<person> — открывающий тег.
</person> — закрывающий тег.
Внутри элемента <person> находятся другие элементы — <name> и <age> .
```

3. Атрибуты (Attributes) Элементы могут иметь атрибуты, которые задаются в открывающем теге.
   Атрибуты состоят из имени и значения, разделённых знаком равенства.
   Атрибуты должны быть заключены в кавычки.

```java
<person name="Alice"age="30"/>

name="Alice" — атрибут name с значением Alice.
age="30" — атрибут age с значением 30.
```

4. Текстовое содержимое (Text Content) Элемент может содержать текст, который находится между его открывающим и
   закрывающим тегами.
   Это основной способ хранения данных в XML.

```java
<greeting>Hello,world!</greeting>

Hello,world! — текстовое содержимое, находящееся внутри элемента <greeting>.
```

5. Комментарии (Comments) В XML можно добавлять комментарии, которые не влияют на обработку данных.
   Комментарии заключаются в <!-- и -->.

```java
<!--Это комментарий -->
<person name="Alice"/>
```

6. Пространства имён (Namespaces) Пространства имён используются для предотвращения конфликтов имен в XML, когда
   используются одинаковые теги, но они могут означать разные вещи.
   Пространства имён задаются с помощью атрибута xmlns

```java
<book xmlns="http://example.com/book">
<title> XML Guide</title>
<author> John Doe</author>
</book>

xmlns="http://example.com/book"указывает, что все элементы внутри
<book>  принадлежат пространству имён http://example.com/book
```

7. CDData (CData) В XML можно использовать CDData для хранения данных, которые должны быть интерпретированы как текст и
   не обрабатываться как элементы XML.
   CData позволяет включать символы, такие как < и &, без необходимости экранирования.

```java
<description><![CDATA[Some<text> that should not be parsed.]]>
</description>

Текст Some <text> that should not be parsed. будет восприниматься
как обычный текст, а не как XML-элементы.
```

8. Декларации сущностей (Entity Declarations)
   В XML можно объявлять сущности, которые будут использоваться в документе. Сущности могут быть встроенными (
   предоставляют простые символы, такие как &, <, >) или внешними (ссылаются на внешние файлы).

```java
<!DOCTYPE greeting [<!ENTITY greetingMessage "Hello, world!">]>
<message>&greetingMessage;</message>

<!ENTITY greetingMessage "Hello, world!"> объявляет сущность с именем
greetingMessage . &greetingMessage; — это ссылка на сущность.
```

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

Преобразование POJO (Plain Old Java Object) в XML и наоборот — это популярная задача, которая может быть решена с
использованием различных библиотек в Java. Одна из наиболее распространённых и удобных библиотек для работы с XML — это
JAXB (Java Architecture for XML Binding). Она позволяет легко сериализовать (преобразовывать) объекты в XML и
десериализовать (преобразовывать) XML в объекты.

1. Добавление зависимости JAXB. Для использования JAXB в вашем проекте, добавьте зависимость в файл pom.xml (для Maven)
   или build.gradle (для Gradle).
2. Пример POJO-класса

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

3. Преобразование из POJO в XML (Сериализация)

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

4. Преобразование из XML в POJO (Десериализация)

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

#### Преобразование с помощью Gson (альтернатива JAXB)

Также можно использовать библиотеку Gson для сериализации и десериализации XML, но для этого нужно дополнительно
настроить преобразование между XML и JSON. Однако JAXB — это более прямолинейный и стандартный способ работы с XML в
Java.

[К оглавлению](#IO)

# 40. Что такое сериализация, десериализация?

Сериализация — это процесс преобразования объекта в поток байтов, который можно передать через сеть, сохранить в файл
или передать между различными приложениями. Основная цель сериализации — сделать объект "плоским", то есть представить
его состояние (поля и их значения) в виде данных, которые можно легко сохранить или передать.

Пример сериализации:

+ Когда вы хотите передать объект через сокет.
+ Когда вам нужно сохранить объект в файл, чтобы потом восстановить его состояние.

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

Десериализация — это процесс восстановления объекта из его сериализованного состояния. Когда объект сериализуется, он
превращается в поток байтов, и десериализация позволяет восстановить оригинальное состояние объекта, прочитав эти байты.

Пример десериализации:

+ Когда вы получаете данные из базы данных или файла и хотите восстановить объект.
+ Когда нужно передать объект по сети и затем снова использовать его в другой части программы.

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

#### Зачем это нужно?

+ Персистентность*: Сериализация позволяет сохранить состояние объектов в файлах или базах данных и затем восстанавливать
  их, обеспечивая долговечность данных.
+ Передача данных: Сериализация позволяет передавать объекты через сеть (например, между клиентом и сервером),
  обеспечивая обмен данными в нужном формате.
+ Удалённые вызовы: В распределённых системах (например, через RMI в Java) объекты часто сериализуются для передачи по
  сети и их последующей десериализации на другом конце.
+ Кэширование: Сохранение состояния объектов для ускорения работы программы.

* Персистентность - возможность сохранения состояния того или иного информационного объекта в течение длительного
  времени. Например, многие компьютерные игры могут записывать текущее состояние пользовательской сессии в файл, который
  может быть восстановлен позже.

#### Примечания:

+ Serializable — интерфейс, который должен реализовать класс, чтобы его объекты могли быть сериализованы.
+ Transient — ключевое слово, которое позволяет исключить поля объекта из процесса сериализации. Если поле помечено как
  transient, оно не будет сериализовано.

[К оглавлению](#IO)

# 41. Что такое регулярные выражения? Зачем они нужны?

Регулярные выражения (regular expressions, или regex) — это мощный инструмент для работы с текстовыми строками. Они
позволяют искать, заменять или проверять строки на соответствие определённому шаблону. Регулярные выражения представляют
собой комбинацию символов и специальных конструкций, которые описывают текстовые шаблоны.

#### Зачем нужны регулярные выражения?

+ Поиск: Регулярные выражения позволяют искать строки, которые соответствуют заданному шаблону. Например, можно искать
  все номера телефонов, адреса электронной почты или другие данные в текстах.
+ Замена: С помощью регулярных выражений можно заменять части строк, которые соответствуют шаблону. Например, заменить
  все вхождения слова "текст" на "статья".
+ Валидация: Регулярные выражения позволяют проверять, соответствует ли строка определённому формату. Например, можно
  проверить, является ли строка валидным номером телефона или адресом электронной почты.
+ Извлечение данных: Регулярные выражения могут использоваться для извлечения части строки, которая соответствует
  шаблону, например, для парсинга текста.

В Java для работы с регулярными выражениями используется класс Pattern и его методы.

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

#### Когда использовать регулярные выражения

Регулярные выражения особенно полезны, когда необходимо:

+ Найти или заменить текст в строках.
+ Проверить формат строки (например, email или телефон).
+ Извлечь части строки (например, парсинг данных).
+ Работать с логами или большими текстами, чтобы найти совпадения.

Однако стоит помнить, что регулярные выражения могут быть сложными для понимания и отладки, поэтому их следует
использовать с осторожностью и там, где они действительно необходимы.

[К оглавлению](#IO)

# 42. Как создать регулярное выражение в Java?

В Java для работы с регулярными выражениями используется класс Pattern из пакета java.util.regex. Регулярные выражения
создаются в виде строковых литералов, а затем компилируются с помощью метода Pattern.compile().

#### Основные шаги для создания регулярного выражения в Java

+ Создание строки с регулярным выражением.
+ Компиляция регулярного выражения в объект Pattern.
+ Использование объекта Matcher для поиска или замены в строках.

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

#### Основные методы класса Pattern

+ compile(String regex) — компилирует строку с регулярным выражением в объект Pattern.
+ compile(String regex, int flags) — компилирует регулярное выражение с флагами (например, игнорирование регистра).
+ matcher(CharSequence input) — создает объект Matcher для заданной строки.

#### Основные методы класса Matcher

+find() — ищет следующее совпадение в строке.

+ matches() — проверяет, соответствует ли вся строка шаблону.
+ group() — возвращает совпавшую часть строки.
+ replaceAll(String replacement) — заменяет все совпадения на строку replacement.

#### Пример использования с флагами

Можно использовать флаги, чтобы изменить поведение регулярного выражения

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

[К оглавлению](#IO)