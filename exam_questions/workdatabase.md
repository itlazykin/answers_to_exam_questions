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

# Настройки Hibernate (реализация JPA)
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

[К оглавлению](#WorkDataBase)

# Что такое драйвер, как он устроен

Драйвер – это переводчик, который превращает команды на Java в понятные СУБД запросы и наоборот.

Драйвер базы данных в Java реализует интерфейс java.sql.Driver. Это стандартный интерфейс, который позволяет драйверу подключаться к базе данных и выполнять с ней операции.



[К оглавлению](#WorkDataBase)

# Что такое jpa, почему не хватает jdbs

[К оглавлению](#WorkDataBase)

# Что такое hibernate

[К оглавлению](#WorkDataBase)

# Что появилось раньше jpa или hibernate

[К оглавлению](#WorkDataBase)

# Какие реализации jpa знаете кроме hibernate

[К оглавлению](#WorkDataBase)

# Как внутри устроен hibernate

[К оглавлению](#WorkDataBase)

# Какие требования предъявляют к сущности чтобы работать с ней с помощью hibernate

[К оглавлению](#WorkDataBase)
