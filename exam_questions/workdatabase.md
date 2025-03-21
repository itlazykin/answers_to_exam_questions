# WorkDataBase

[Какой инструмент есть в java для работы с базой данных](#какой-инструмент-есть-в-java-для-работы-с-базой-данных)

[Что нужно прописать в datasource для подключения к бд](#что-нужно-прописать-в-datasource-для-подключения-к-бд)

[Что такое драйвер, как он устроен](#что-такое-драйвер-как-он-устроен)

[Что такое jpa, почему не хватает jdbs](#что-такое-jpa-почему-не-хватает-jdbs)

[Что такое hibernate](#что-такое-hibernate)

[Что появилось раньше jpa или hibernate](#что-появилось-раньше-jpa-или-hibernate)

[Какие реализации jpa знаете кроме hibernate](#какие-реализации-jpa-знаете-кроме-hibernate)

[Как внутри устроен hibernate](#как-внутри-устроен-hibernate)

[Какие требования предъявляют к сущности чтобы работать с ней с помощью hibernate](#какие-требования-предъявляют-к-сущности-чтобы-работать-с-ней-с-помощью-hibernate)

# Какой инструмент есть в java для работы с базой данных

+ JDBC(Java Database Connectivity) — это стандартный API для взаимодействия с реляционными базами данных. Он позволяет
  выполнять SQL-запросы, получать
  результаты и управлять транзакциями. JDBC требует написания SQL-кода вручную, и работает на низком уровне, но даёт
  полный контроль над взаимодействием с базой данных.
+ JPA(Java Persistence API) — это спецификация для объектно-реляционного отображения (ORM), которая упрощает работу с
  базой данных, превращая
  объекты Java в записи в таблицах базы данных и наоборот. JPA значительно упрощает работу по сравнению с JDBC, так как
  позволяет работать с базой данных на уровне объектов, а не с SQL-запросами. Пример реализации JPA — Hibernate.
+ В Spring есть проект Spring Data, который упрощает работу с JPA и другими технологиями для доступа к данным. Он
  предоставляет готовые решения для работы с реляционными и нереляционными базами данных, упрощает создание репозиториев
  и автоматическую генерацию запросов.
+ Spring JDBC Это набор инструментов в рамках Spring Framework, который предоставляет абстракцию для работы с JDBC,
  упрощая
  управление соединениями и обработку исключений, но при этом оставляя возможность работы с SQL-запросами напрямую.

[К оглавлению](#WorkDataBase)

# Что нужно прописать в datasource для подключения к бд

В JDBC мы подключаемся через DriverManager, передавая URL, логин и пароль. В JPA (через Spring) используется DataSource,
а настройки указываются в application.properties или application.yml, после чего Spring сам создаёт соединение и
управляет транзакциями.

```java
Пример подключения в JDBC:

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class JdbcExample {
    public static void main(String[] args) {
        String url = "jdbc:postgresql://localhost:5432/mydb";
        String user = "myuser";
        String password = "mypassword";

        try (Connection connection = DriverManager.getConnection(url, user, password)) {
            System.out.println("Подключение успешно!");
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}

В JPA

spring.datasource.url=jdbc:postgresql://localhost:5432/mydb
spring.datasource.username=myuser
spring.datasource.password=mypassword
spring.datasource.driver-class-name=org.postgresql.Driver

#

Настройки Hibernate(реализация JPA)

spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

[К оглавлению](#WorkDataBase)

# Что такое драйвер, как он устроен

Драйвер – это то, что позволяет работать с бд (поддерживать подключения, выполнять запросы и т.д.). Для каждой БД есть
свой драйвер. Чтобы добавить драйвер в проект необходимо добавить зависимость на этот самый драйвер.

Драйвер реализует интерфейс Driver и отвечает за установление соединения, выполнение SQL-запросов, передачу данных и
управление транзакциями.

Когда вызывается DriverManager.getConnection(), драйвер создает соединение с базой данных. Драйвер переводит SQL-запросы
из Java-кода в формат, понятный конкретной базе.
Полученные результаты запросов драйвер конвертирует в объекты Java. Драйвер работает как посредник между приложением и
базой данных, переводя запросы из Java в SQL и наоборот

[К оглавлению](#WorkDataBase)

# Что такое jpa, почему не хватает jdbs

JPA (Java Persistence API) — это стандартная спецификация для работы с базами данных в Java через объектно-реляционное
преобразование (Object-Relational Mapping). Она упрощает взаимодействие с базой данных, позволяя работать с данными как с объектами, без
необходимости вручную писать SQL-запросы.

Почему JDBC недостаточно?
JDBC — это низкоуровневый инструмент, который требует явного написания SQL-запросов, обработки соединений, транзакций,
маппинга данных между таблицами и объектами вручную. Это приводит к большому количеству шаблонного кода.

Чем JPA лучше JDBC?

+ Вместо работы с ResultSet, мы работаем с сущностями (@Entity классы).
+ JPA сама преобразует(мапит) объекты в SQL-запросы и обратно.
+ JPA автоматически управляет транзакциями.
+ JPA использует кеширование для ускорения работы с данными.
+ Можно менять СУБД без значительных изменений кода.

```java
JPA:

@Entity
public class User {
    @Id
    @GeneratedValue
    private Long id;
    private String name;
}

User user = entityManager.find(User.class, 1L);


JDBC:

Connection conn = DriverManager.getConnection(url, user, password);
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM users WHERE id = 1");

while(rs.next()){
String name = rs.getString("name");
}
```

[К оглавлению](#WorkDataBase)

# Что такое hibernate

Hibernate — это самая популярная реализация JPA, которая позволяет работать с базами данных через ORM. Он упрощает
работу с SQL, поддерживает кэширование, ленивую загрузку и автоматически маппит Java-объекты на таблицы базы данных.

```java
 Класс-сущность

@Entity

public class User {
    @Id
    @GeneratedValue
    private Long id;
    private String name;
}

2.Сохранение объекта
в БД

Session session = sessionFactory.openSession();
session.beginTransaction();
session.save(new User("John"));
session.getTransaction().commit();
session.close();
```

[К оглавлению](#WorkDataBase)

# Что появилось раньше jpa или hibernate

Hibernate появился раньше JPA. Hibernate был создан в 2001 году как независимый ORM-фреймворк, а JPA была представлена в
2006 году как стандартная спецификация для работы с базами данных. Hibernate впоследствии стал одной из самых популярных
реализаций JPA

[К оглавлению](#WorkDataBase)

# Какие реализации jpa знаете кроме hibernate

Помимо Hibernate, существуют реализации JPA, такие как EclipseLink (официальная реализация JPA от Eclipse Foundation ),
OpenJPA (от Apache) и DataNucleus (поддерживает NoSQL).

[К оглавлению](#WorkDataBase)

# Как внутри устроен hibernate

Hibernate использует собственный язык запросов HQL, который напоминает SQL, но работает с объектами, а не с таблицами.
Hibernate предоставляет механизмы для маппинга объектов на таблицы в базе данных, для выполнения запросов к базе данных
и для управления транзакциями. Hibernate использует пул соединений (Connection Pool) для эффективного управления
подключениями к базе данных:
Вместо того чтобы открывать и закрывать соединение для каждого запроса, Hibernate берет соединение из пула, использует
его и возвращает обратно.

[К оглавлению](#WorkDataBase)

# Какие требования предъявляют к сущности чтобы работать с ней с помощью hibernate

Чтобы класс был сущностью в Hibernate, он должен быть помечен @Entity, иметь @Id как первичный ключ, конструктор без
аргументов, а также public геттеры/сеттеры. Нельзя использовать final классы и поля, так как Hibernate работает через
прокси это динамические подклассы сущностей, которые подгружают данные только при первом доступе. Прокси позволяют
экономить ресурсы, но могут привести к LazyInitializationException, если Session уже закрыта.
Hibernate использует аннотации или xml-конфиг для понимания, как объекты Java должны быть отображены на таблицы базы данных.

[К оглавлению](#WorkDataBase)
