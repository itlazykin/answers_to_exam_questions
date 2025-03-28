## GC

[1. Чем Java отличается от C++?](#1-Чем-Java-отличается-от-C)

[2. Что такое менеджер памяти?](#2-что-такое-менеджер-памяти)

[3. Какой механизм используется в Java для управления памятью?](#3-какой-механизм-используется-в-java-для-управления-памятью)

[4. Опишите процесс работы сборщика мусора.](#4-опишите-процесс-работы-сборщика-мусора)

[5. Какие алгоритмы сборщика вы знаете?](#5-какие-алгоритмы-сборщика-вы-знаете)

[6. Чем отличаются сборщики мусора?](#6-чем-отличаются-сборщики-мусора)

[7. Расскажите про утилиты для анализа памяти?](#7-расскажите-про-утилиты-для-анализа-памяти)

[8. Что такое ссылки?](#8-что-такое-ссылки)

[9. Какие типы ссылок Вы знаете?](#9-какие-типы-ссылок-вы-знаете)

[10. Чем эти ссылки отличаются?](#10-чем-эти-ссылки-отличаются)

[11. Расскажите про String pool и Integer pool (Integer cache).](#11-расскажите-про-string-pool-и-integer-pool-integer-cache)

[12. Расскажите о методе String.intern().](#12-расскажите-о-методе-stringintern)

[13. Расскажите, что такое профайлер.](#13-расскажите-что-такое-профайлер)

[14. Расскажите, как использовать VisualVM.](#14-расскажите-как-использовать-visualvm)

[15. Расскажите, чем отличается sampling от profiling? (Это типы аудита. Режим работы в профайлере)](#15-расскажите-чем-отличается-sampling-от-profiling-это-типы-аудита-режим-работы-в-профайлерерасскажите-чем-отличается-sampling-от-profiling-это-типы-аудита-режим-работы-в-профайлере)

[16. Расскажите о методе finalize().](#16-расскажите-о-методе-finalize)

[17. Расскажите о методе clone(). Что такое Deep clone and Shallow clone?](#17-расскажите-о-методе-clone-что-такое-deep-clone-and-shallow-clone)

[18. Расскажите о Stack, Heap и Metaspace.](#18-расскажите-о-stack-heap-и-metaspace)

[19. Что такое ClassLoader? Перечислите основные реализации ClassLoader.](#19-что-такое-classloader-перечислите-основные-реализации-classloader)

[20. Расскажите иерархию штатных загрузчиков классов в Java. Какой загрузчик находится в корне иерархии?](#20-расскажите-иерархию-штатных-загрузчиков-классов-в-java-какой-загрузчик-находится-в-корне-иерархии)

[21. Какой загрузчик классов нельзя получить методом getClassLoader()? Почему?](#21-какой-загрузчик-классов-нельзя-получить-методом-getclassloader-почему)

[22. Расскажите алгоритм поиска и загрузки класса в JVM.](#22-расскажите-алгоритм-поиска-и-загрузки-класса-в-jvm)

# 1. Чем Java отличается от C++?

##### Java

1) код выполняется в JVM + GC
2) легкопортируема благодаря JVM
3) менее быстрый из-за JVM

##### С++

1) ручная работа с памятью
2) зависимость от платформы, необходимость изменений или перекомпиляции
3) быстрый благодаря "близости к железу"

[К оглавлению](#GC)

# 2. Что такое менеджер памяти?

Это программа обрабатывающая запросы на выделение и освобождение оперативной памяти.

[К оглавлению](#GC)

# 3. Какой механизм используется в Java для управления памятью?

Сборка мусора выполняется сборщиком мусора (Garbage Collector (GC)). GC – часть JVM,
прикладная программа, которая занимается очищением памяти. Прежде чем удалить объект, нужно знать, где он находится:

+ Важное отступление, выбор «поколенческой» (generational) модели памяти сделан не спроста. Опытным путем было доказано,
  что большинство объектов не живут долго. Это заключение, позволяет сделать young generation небольшим, а в old
  generation хранить объекты действительно «живущие» дольше обычного, тем самым эффективно использовать память.
  ![img](https://github.com/itlazykin/answers_to_exam_questions/blob/main/main/resources/meminjava.png)

#### Структура памяти в JVM:

+ Stack (Не управляется сборщиком мусора)
    + Permanent Generation — содержит необходимые для управления программой метаданные классов,
      в том числе метаданные о созданных объектах, методах и т.п.
    + Code Cache — используемая JVM память при включенной JIT-компиляции
      (в этой области памяти кешируется скомпилированный платформенно-зависимый код)

+ Heap - куча (тут работает GC)
    + New (Yang) Generation - хранит короткоживущие объекты.
        + Eden Space — сюда распределяются среднестатистические объекты*. Если нет места запускается малая сборка
          мусора (minor GC).
        + Survivor Space — точнее их два, S1 и S2, и они меняются ролями.
          Хранятся перемещенные из Eden Space объекты, признанные живыми во время сборки мусора (без разницы малой или
          полной).
          Объекты, пережившие несколько сборок мусора, перемещаются в следующую сборку Tenured Generation.
    + Old (Tenured) Generation - хранит долгоживущие объекты. Когда данная область памяти заполняется,
      выполняется полная сборка мусора (full GC).

#### Как сборщик мусора понимает, какие объекты нужно удалить?

Основным фактором здесь выступает тип ссылки. GC видит, что мы используем «обычные» ссылки. Далее он смотрит на
достижимость объекта по ссылке. Это значит, что если мы не можем получить к нему доступ из программы, т.е. у нас нет
ссылки на него, то он помечается как мусор и будет удален при следующей сборке мусора.

#### Сборка мусора

Сборка мусора происходит, когда заполнена вся область памяти. Память делится на два поколения, поэтому есть два типа
сборки мусора: minor GC и major GC. Первый происходит, когда переполняется young generation, второй, когда переполняется
область из old generation.

#### Стадии, которые проходят объекты до сборки мусора.

1. Объект рождается. Во время исполнения JVM видит, что стоит оператор new. Происходит выделение памяти под объект и
   возврат ссылки, которая будет ссылаться на занятый участок памяти. Все объекты рождаются в eden

![img](https://github.com/itlazykin/answers_to_exam_questions/blob/main/main/resources/mem1.png)

2. Этап 1 выполняет до тех пор, пока не будет заполнен eden. Когда eden заполнен происходит minor GC(малая сборка
   мусора) — это процесс в сборке мусора в Java, который запускается, когда область памяти Young Generation (молодое
   поколение) заполняется.

![img](https://github.com/itlazykin/answers_to_exam_questions/blob/main/main/resources/mem2.png)

3. Объекты, у которых уже нет ссылки удаляются.

![img](https://github.com/itlazykin/answers_to_exam_questions/blob/main/main/resources/mem3.png)

4. Объекты, у которых есть ссылки попадают в survivor space из eden. Причем survivor space делиться на две части. Между
   этими частями происходит перемещения объектов. В один момент времени одна из частей пуста, чтоб мочь вместить объекты
   пришедшие из eden.

![img](https://github.com/itlazykin/answers_to_exam_questions/blob/main/main/resources/mem4.png)

5. Объекты, которые уже были в одной части survivor space, перемещаются в другую, при этом растет их «возраст» (age).
   Сам процесс, перемещения объектов из различных частей survivor space и увеличения их возраста называется
   «взрослением» (aging).

![img](https://github.com/itlazykin/answers_to_exam_questions/blob/main/main/resources/mem5.png)

6. бъекты, которые достигли определенного возраста попадают в old generation. Этот процесс называется «продвижением»
   promotion.

![img](https://github.com/itlazykin/answers_to_exam_questions/blob/main/main/resources/mem6.png)

7. Этапы 1-6 происходят до тех пока не будет заполнен old generation, причем по ходу будут происходить minor GC, для
   очищения young generation.
8. Когда old generation заполняется производиться major GC
9. Этапы 1-7 происходят на протяжении работы программы

*объекты-акселераты, размер которых настолько велик, что создавать их в Eden,
а потом таскать за собой по Survivor’ам слишком накладно, размещаются сразу в Tenured Generation.

[К оглавлению](#GC)

# 4. Опишите процесс работы сборщика мусора.

1. **Minor GC (молодежная сборка)**:

- Этот тип сборки мусора сосредотачивается на молодых объектах, которые только что были созданы и обычно живут недолго.
  Эти объекты обычно размещаются в поколении молодых объектов (Young Generation).
- В процессе Minor GC происходит сборка мусора внутри поколения молодых объектов. Мертвые объекты удаляются, а выжившие
  объекты перемещаются в другое подпоколение (например, из Eden Space в Survivor Space).
- Minor GC происходит гораздо чаще, чем Major GC, и его цель - минимизировать простой приложения.

2. **Major GC (старшая сборка)**:

- Этот тип сборки мусора сосредотачивается на объектах, которые считаются "старыми" или "долго живущими".
  Эти объекты обычно находятся в поколении старых объектов (Old Generation).
- В процессе Major GC происходит сборка мусора внутри поколения старых объектов.
  Этот тип сборки мусора менее часто вызывается, чем Minor GC, и обычно сопровождается более длительным временем простоя
  приложения.
- Major GC направлен на очистку памяти от объектов, которые прожили длительное время и не были удалены в процессе Minor
  GC.

[К оглавлению](#GC)

# 5. Какие алгоритмы сборщика вы знаете?

Сборщики мусора различаются относительно характеристик какими они обладают.

+ Последовательное (Serial) vs параллельное (Parallel) исполнение сборки мусора. Для того, чтобы очистить память нужно
  остановить приложение - событие Stop The World.
  Причем сам процесс сборки может быть ускорен за счет использования нескольких процессоров, если они присутствуют
  физически.
  Если мы используем последовательную сборку, то она выполняется только в одном потоке и задействует только один
  процессор, что увеличивает время сборки.
  С другой стороны мы можем использовать несколько процессоров за счет распараллеливания сборки, что уменьшает время
  сборки, ценой затрат ресурсов (процессоров) и некоторых накладных расходов (overhead), требуемых для организации
  работы потоков исполнения (Thread).
+ Параллелизм (Concurrency) vs Stop The World. Еще одним способом уменьшения времени пауз является использование
  параллелизма. Данный подход заключается в том, что сборщик мусора работает одновременно с самим приложением. При этом
  он не ждет пока heap заполнится полностью, он периодически производит "мелкие" сборки.
  Причем эти сборки тоже вызывают событие Stop The World, но по времени оно занимает меньше чем если бы сборщик мусора
  чистил бы полностью heap.
  Использование данного подхода оправдано в системах, где требуется минимальный отклик от приложения и не допустимы
  долгие паузы.
  Однако эти минимальные паузы достигаются за счет того, что сборщик мусора требует heap больше.

#### Виды сборок мусора.

После того как сборщик мусора определил, что нужно удалить объекты, он может пользоваться следующими сборками:
Compacting, Non-compacting and Copying.

+ Compacting (Compact с англ. уплотнить): Собирает "живые" объекты в одном месте и очищает оставшуюся часть памяти, где
  находятся объекты, которые нужно уничтожить.
    + Преимущество такого подхода - легко можно выделять память для новых объектов.
    + Недостаток - требуется время на компоновку объектов в одном месте.
+ Non-compacting. Удаляет объекты по месту. Т.е. он понимает, что данную часть памяти занимает объект, который нужно
  удалить, и чистит эту часть памяти.
    + Преимущество: не нужно производить лишние действия, нужно просто удалить объекты.
    + Недостаток: при создании объекта нужно находить для него подходящее место, что приводит к фрагментации памяти (это
      когда большая часть вашей памяти выделена в большом количестве несмежных блоков, оставляя приличный процент вашей
      общей памяти нераспределенной, но при этом непригодной для большинства типичных сценариев использования памяти),
      то есть много свободных мест памяти между занятыми ячейками, но из-за малых ее размеров, ее практически ничем не
      занять, и эта память простаивает.
+ Copying. Копирует "живые" объекты в отдельную часть памяти, очистив старую часть, где они были (С этим типом вы
  встречались в прошлом задании).
    + Преимущество: нет препятствий выделению памяти.
    + Недостаток: требуется время на копирование.

1. `Serial GC`

+ Назначение: Однопоточный сборщик мусора, подходит для приложений с небольшими кучами и работающих в однопоточной
  среде.
+ Алгоритм:
  Использует копирование (Copying) для Young Generation.
  Маркировка-вычищение-компактификация (Mark-Sweep-Compact) для Old Generation.
+ Особенности:
  Приостанавливает все потоки приложения (Stop-the-World, STW) во время сборки.
  Прост и эффективен для малых куч.
+ Ключ: -XX:+UseSerialGC

2. `Parallel GC` (Throughput Collector)

+ Назначение: Многопоточный сборщик мусора для приложений с высокой пропускной способностью (например, серверные
  приложения).
+ Алгоритм:
  Для Young Generation используется копирование.
  Для Old Generation — маркировка-вычищение-компактификация.
+ Особенности:
  Минимизирует общее время, затраченное на сборку, за счёт использования нескольких потоков.
  Все ещё вызывает паузы STW.
+ Ключ: -XX:+UseParallelGC

3. `CMS (Concurrent Mark-Sweep)`

+ Назначение: Минимизирует паузы, подходит для интерактивных приложений.
+ Алгоритм:
  Использует маркировку и вычищение (Mark-Sweep).
  Выполняет большинство работы одновременно с приложением.
+ Особенности:
  Нет компактификации памяти, что может привести к её фрагментации.
  Устарел, начиная с Java 9, заменён на G1.
+ Ключ: -XX:+UseConcMarkSweepGC

4. `G1 GC (Garbage First GC)`

+ Назначение: Подходит для больших куч и приложений с требованиями к минимальным паузам.
+ Алгоритм:
  Разделяет кучу на регионы.
  Сначала очищает регионы с наибольшим количеством мусора (Garbage First).
  Использует комбинацию маркировки, копирования и компактификации.
+ Особенности:
  Снижает паузы за счёт распределения работы на мелкие порции.
  Частично выполняет сборку параллельно с работой приложения.
+ Ключ: -XX:+UseG1GC

5. `ZGC (Z Garbage Collector)`

+ Назначение: Для приложений с большими кучами (до терабайтов) и строгими требованиями к минимальным паузам.
+ Алгоритм: Использует маркировку и копирование. Работает преимущественно параллельно с приложением.
+ Особенности:
  Паузы обычно не превышают 10 миллисекунд.
  Фрагментация памяти минимальна.
  Требует поддержки современных процессоров.
+ Ключ: -XX:+UseZGC

| GC          | Цель                           | Подходит для                  | Паузы          | Примечания                                     |
|-------------|--------------------------------|-------------------------------|----------------|------------------------------------------------|
| Serial GC   | Однопоточные приложения        | Маленькие кучи                | Длинные        | Serial, Stop The World, Copying                |
| Parallel GC | Высокая пропускная способность | Многопоточные серверы         | Средние        | Parallel, Stop The World, Copying              |
| CMS         | Минимизация пауз               | Реалтайм-приложения           | Средние        | Parallel, Concurrent, Copying. Убран с JDK 14. |
| G1 GC       | Минимизация пауз               | Большие кучи                  | Короткие       | Parallel, Concurrent, Copying. Замена CMS      |
| ZGC         | Минимизация пауз               | Огромные кучи (до терабайтов) | Очень короткие | Parallel, Concurrent, Copying                  |

[К оглавлению](#GC)

# 6. Чем отличаются сборщики мусора?

- Максимальная задержка — максимальное время, на которое сборщик приостанавливает выполнение программы для выполнения
  одной сборки. Такие остановки называются _stop-the-world_ (или _STW_).
- Пропускная способность — отношение общего времени работы программы к общему времени простоя, вызванного сборкой
  мусора, на длительном промежутке времени.
- Потребляемые ресурсы — объем ресурсов процессора и/или дополнительной памяти, потребляемых сборщиком.

[К оглавлению](#GC)

# 7. Расскажите про утилиты для анализа памяти?

1) jps - показывает pid приложения
2) jmap - позволяет сделать дамп памяти
3) jstat - показывает сводную информацию о состоянии памяти
4) jconsole - имеет окошки, наглядно отображает данные
5) visualVM - ещё лучше jconsole

[К оглавлению](#GC)

# 8. Что такое ссылки?

Ссылки представляют собой способ обращения к объектам в памяти. Когда вы создаёте объект в Java, вы фактически создаёте
блок памяти в куче, а переменная, которой вы присваиваете этот объект, хранит ссылку на его адрес в памяти.

#### Как работают ссылки в Java

Ссылки в Java представляют собой специальные объекты, которые позволяют вам управлять временем жизни других объектов в
памяти и взаимодействовать с процессом сборки мусора.
Они используются для отслеживания и контроля доступности объектов в памяти.

[К оглавлению](#GC)

# 9. Какие типы ссылок Вы знаете?

1. **Strong Reference (Сильная ссылка)**:

- Сильная ссылка - это наиболее распространенный тип ссылок в Java. Когда объект имеет хотя бы одну сильную ссылку, он
  считается активным и не подлежит сборке мусора.
- Пример: `Object obj = new Object();`

2. **Soft Reference (Мягкая ссылка)**:

- Мягкая ссылка позволяет объекту существовать до тех пор, пока для него есть доступ через сильные ссылки.
  Когда сборщик мусора решает, что память исчерпана, он может начать удалять объекты с мягкими ссылками.
- Пример: `SoftReference<Object> softRef = new SoftReference<>(new Object());`

3. **Weak Reference (Слабая ссылка)**:

- Слабая ссылка также позволяет объекту существовать до тех пор, пока для него есть доступ через сильные ссылки.
  Однако, даже если есть слабая ссылка, объект может быть удален сразу при следующей сборке мусора.
- Пример: `WeakReference<Object> weakRef = new WeakReference<>(new Object());`

4. **Phantom Reference (Фантомная ссылка)**:

- Фантомная ссылка позволяет отслеживать, когда объект был удален сборщиком мусора, но не предоставляет доступа к самому
  объекту.
  Она используется в сочетании с ReferenceQueue для выполнения дополнительных действий при удалении объекта.
- Пример: `PhantomReference<Object> phantomRef = new PhantomReference<>(new Object(), referenceQueue);`

5. **ReferenceQueue**:

- ReferenceQueue - это специальный механизм, который позволяет отслеживать удаление объектов с помощью слабых и
  фантомных ссылок.
  Когда объект, на который указывает слабая или фантомная ссылка, становится доступным для сборки мусора, ссылка
  помещается в очередь ReferenceQueue.

[К оглавлению](#GC)

# 10. Чем эти ссылки отличаются?

Сильные, слабые, мягкие и фантомные ссылки в Java отличаются степенью "удержания" объекта в памяти, то есть тем, как они
влияют на возможность удаления объекта сборщиком мусора (Garbage Collector, GC).

| Тип ссылки | Удерживает объект в памяти?          | Когда объект удаляется?           | Основные применения                |
|------------|--------------------------------------|-----------------------------------|------------------------------------|
| Сильная    | Да                                   | Никогда, пока есть сильные ссылки | Обычная работа с объектами         |
| Слабая     | Нет                                  | Когда больше нет сильных ссылок   | Кеши, где данные можно воссоздать  |
| Мягкая     | Условно (пока есть свободная память) | При нехватке памяти               | Memory-sensitive кеши              |
| Фантомная  | Нет                                  | Сразу после завершения работы GC  | Освобождение ресурсов, логирование |

[К оглавлению](#GC)

# 11. Расскажите про String pool и Integer pool (Integer cache).

String pool - это специальная область памяти в куче (heap), куда сохраняются только уникальные значения строк.
Строка, созданная с помощью конструктора через ключевое слово new, будет создана непосредственно в heap

Integer pool - В нем хранятся числа от -128 до 127 включительно, то есть пул Integer хранит все числа, которые
помещаются в тип byte.
Суть пула Integer в оптимизации, также как и пула строк. Когда мы создаем объекты Integer, то все объекты, входящие в
указанный диапазон, будут взяты из пула Integer.
Благодаря пулу Integer системе не придется создавать новые объекты, так как они уже есть в пуле. Этого диапазона чисел
достаточно для оптимизации большинства вычислений.

| Характеристика      | String Pool                   | Integer Pool                  |
|---------------------|-------------------------------|-------------------------------|
| Тип данных          | Только строки                 | Автобоксинг для Integer       |
| Диапазон значений   | Все строки литералы           | От -128 до 127 (по умолчанию) |
| Механизм управления | Автоматически управляется JVM | Управляется через кеш         |
| Метод доступа       | intern()                      | valueOf()                     |

[К оглавлению](#GC)

# 12. Расскажите о методе String.intern().

Данный метод гарантирует, что возвращенная ссылка будет указывать на объект, находящийся в пуле строк.
Те можно перенести созданную строку heap в srting pool.

[К оглавлению](#GC)

# 13. Расскажите, что такое профайлер.

Пофилировщик (profiler) - это специальная программа, с помощью которой можно оценить, при выполнении каких операций
и в каком количестве потребляются ресурсы при работе нашего приложения.
Профилировщик отслеживает конструкции и операции байт-кода на уровне виртуальной машины Java. Сюда входят создание
объекта, выполнение методов, состояние нитей, сборка мусора и т.д.
Также с помощью профайлера можно отслеживать производительность и загрузку ЦП и использование памяти приложением.

[К оглавлению](#GC)

#### 14. Расскажите, как использовать VisualVM.

Открывает VisualVM, выбираешь процесс, ожидаешь когда загрузится профайлер, смотришь на данные.

[К оглавлению](#GC)

# 15. Расскажите, чем отличается sampling от profiling? (Это типы аудита. Режим работы в профайлере)Расскажите, чем отличается sampling от profiling? (Это типы аудита. Режим работы в профайлере)

Сэмплинг - это выборка. Запуск выборки работы процесса осуществляется нажатием на кнопку CPU. Сохранить данные можно
кнопкой Snapshot.
Выборка по загрузке памяти делается аналогично - нажать кнопку Memory, а после сохранить кнопкой Snapshot.

Профайлин - более точный метод чем сэмплинг блягодаря инструментированию.

Инструментирование - это добавление байткода в существующий байткод, для сбора дополнительной информации о работе
методов и тд.

[К оглавлению](#GC)

# 16. Расскажите о методе finalize().

1. finalize() можно использовать только в двух случаях:
   1.1. Проверка/подчистка ресурсов с логированием
   1.2. При работе с нативным кодом, который не критичен к утечке ресурсов
2. finalize() замедляет работу GC по очистке объекта в 430 раз
3. finalize() может быть не вызван

[К оглавлению](#GC)

# 17. Расскажите о методе clone(). Что такое Deep clone and Shallow clone?

shallow clone: Если нам нужно создать копию объекта, можно использовать метод clone() класса Object.
Для реализации копирования с помощью clone() класс, копию которого нужно сделать, должен реализовывать интерфейс
Cloneable.
Данный интерфейс не содержит никаких методов. Это маркер, сигнализирующий системе о том, что этот класс можно
клонировать.

Класс, поля которого содержали только примитивные значения, при поверхностном копировании такого класса будет создан
полностью уникальный объект.
Если же в копируемом классе присутствуют поля, которые хранят ссылки на объекты, то в новый объект будут скопированы
только сами ссылки на эти объекты, поэтому копирование с помощью метода clone() называется _поверхностным_
_копированием_.

deep clone: Глубокое копирование создает клон, полностью независимый от исходного объекта, то есть изменения в
скопированном объекте не повлияют на исходный объект.

все ссылочные типы данных должны реализовывать Cloneable

[К оглавлению](#GC)

# 18. Расскажите о Stack, Heap и Metaspace.

Стек хранит значения примитивных типов, которые создаются в методах, и ссылки на объекты в heap, на которые ссылаются
методы.
Когда в программе вызывается метод, JVM выделяет память в стеке для вызова этого метода. В этой памяти будут храниться
значения примитивных типов и ссылки на объекты в куче.
Стек организован по принципу LIFO - Last In First Out (Последним пришел, первым вышел).
При вызове каждого метода, содержащего примитивные типы или ссылки на объекты, в стеке выделяется память, которая хранит
эти переменные и ссылки этого метода.
Данные, хранящиеся в этой области памяти, имеют область видимости, которая ограничена телом метода, под который данная
часть памяти выделена.
Когда в программе выполняется какой-либо метод, компилятор может получить доступ к переменным только этого метода. (К
статическим переменным доступ есть из любого места программы).
При выполнении цепочки методов в момент передачи управления вызываемому методу программа запоминает состояние выполнения
текущего метода,
создает новую область памяти в стеке под вызываемый метод, создает там переменные и ссылки вызываемого метода, и
передаёт ему управление.
Если в вызываемом методе придется вызывать еще один метод, то эта цепочка действий повторяется.

В heap хранятся сами объекты, под которые динамически выделяется память во время выполнения программы.

Metaspace - Это отдельная область памяти, выделенная под хранение статической информации приложения. Например,
метаданные загруженных классов.
Metaspace автоматически расширяется при заполнении. Эта область так же доступна для сборщика мусора, как и heap.
Сборщик удаляет ненужные классы из памяти, когда область для хранения метаданных заполнена.

#### Ключевые различия между Stack, Heap и Metaspace

| Характеристика   | Stack	                               | Heap                   | Metaspace          |
|------------------|--------------------------------------|------------------------|--------------------|
| Роль             | Локальные переменные, вызовы методов | Долговременные объекты | Метаданные классов |
| Управление       | Автоматическое, с завершением метода | Сборщик мусора         | Сборщик мусора     |
| Размер           | Задаётся на старте JVM               | Динамически растёт     | Динамически растёт |
| Скорость доступа | Очень высокая                        | Высокая                | Высокая            |
| Содержит         | Примитивы, ссылки на объекты	        | Объекты, их поля       | Метаданные классов |

+ Stack: используется для выполнения методов и локальных переменных. Очень быстро очищается после завершения вызова.
+ Heap: для хранения объектов и данных, которые требуют более долгого времени жизни. Управляется сборщиком мусора.
+ Metaspace: для хранения информации о классах и методах. Динамически масштабируется, не имеет фиксированного размера.

[К оглавлению](#GC)

# 19. Что такое ClassLoader? Перечислите основные реализации ClassLoader.

**ClassLoader** (загрузчик классов) в Java - это механизм, который загружает классы в Java во время выполнения.

1. **Bootstrap ClassLoader**:

    - Это корневой загрузчик классов, который загружает классы из директории `jre/lib` и из JAR-файлов в папке
      `jre/lib/ext`.
      Он не имеет родительского загрузчика и является самым высоким в иерархии загрузчиков.
2. **Extension ClassLoader**:

    - Этот загрузчик классов наследует от Bootstrap ClassLoader и загружает классы из папки `jre/lib/ext`.
3. **System ClassLoader (Application ClassLoader)**:

    - Этот загрузчик классов загружает классы из CLASSPATH и является родителем для загрузчиков, созданных
      пользовательским кодом.
      Он загружает классы из директорий и JAR-файлов, указанных в переменной окружения CLASSPATH.
4. **Custom ClassLoaders (Пользовательские загрузчики классов)**:

    - Пользовательский код может создавать собственные загрузчики классов, наследуясь от `java.lang.ClassLoader`.
      Эти пользовательские загрузчики могут загружать классы из разных источников, таких как файлы, базы данных и другие
      источники.
      Пользовательские загрузчики могут быть полезными, например, при реализации модульной системы.

[К оглавлению](#GC)

# 20. Расскажите иерархию штатных загрузчиков классов в Java. Какой загрузчик находится в корне иерархии?

В Java загрузчики классов организованы в иерархическую структуру с делегированием загрузки. Каждый загрузчик классов
делегирует задачу загрузки своему родителю перед тем, как попытаться загрузить класс самостоятельно. Это помогает
избежать конфликтов, например, когда системный класс и пользовательский имеют одно и то же имя.

#### Иерархия штатных ClassLoaders

Bootstrap class loader -> Extension / Platform CL -> System / Application CL -> userCustom CL

[К оглавлению](#GC)

# 21. Какой загрузчик классов нельзя получить методом getClassLoader()? Почему?

Реализация базового загрузчика содержится в самой JVM, поэтому мы не можем её получить. При попытке получения загрузчика
класса, который был загружен базовым загрузчиком, мы получим null

[К оглавлению](#GC)

# 22. Расскажите алгоритм поиска и загрузки класса в JVM.

Попытка загрузки класса происходит таким образом:
у каждого загрузчика есть список классов, который он уже загружал (кэш). Сначала производится **проверка**, есть ли в
кэше загрузчика `System / Application` (в текущем) требуемый класс.
Если его там нет, задача делегируется родителю текущего загрузчика, то есть загрузчику `Extension / Platform`. Если в
нём тоже нет, то задача делегируется дальше родителю текущего загрузчика - в загрузчик `Bootstrap`.
Если в кэше какого-либо из этих загрузчиков есть запрашиваемый класс (класс уже был загружен ранее), то возвращается
объект Class данного класса, и поиск завершается.
Если ни у одного из этих загрузчиков в кэше нет запрашиваемого класса (то есть этот класс еще не загружался), то
начинается попытка **загрузки** запрашиваемого класса в обратном порядке от корневого до текущего.
Сначала загрузчик `Bootstrap` пытается загрузить запрашиваемый класс.
Если в нём его нет, то этот класс пытается загрузить загрузчик `Extension / Platform`, далее `System / Application`, и
если ни один из загрузчиков не загрузил запрашиваемый класс, то выбрасывается исключение `ClassNotFoundException`.
Если же класс удалось загрузить какому-либо из загрузчиков, то на этом работа по загрузке этого класса прекращается.

[К оглавлению](#GC)
