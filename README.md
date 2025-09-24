# Acceder a Datos con JPA (Spring Data JPA)

Este proyecto demo enseña cómo construir una aplicación con Spring Boot que usa Spring Data JPA para guardar y recuperar datos en una base de datos relacional (una base en memoria H2 para fines de demostración).

---

## 📦 Requisitos

- Java 17 o superior
- Maven 3.5+
- IDE de tu preferencia (IntelliJ, VSCode, Spring Tool Suite, etc.)

---

## 🚀 Cómo iniciar el proyecto

1. Usa **Spring Initializr** para generar un proyecto con las dependencias:

   - _Spring Data JPA_
   - _H2 Database_

2. O clona directamente este repositorio:

   ```bash
   git clone https://github.com/spring-guides/gs-accessing-data-jpa.git
   cd gs-accessing-data-jpa/initial
   ```

---

## 🧱 Estructura clave

Estos son los componentes principales del proyecto:

- **Entidad `Customer`**
  Clase que representa los clientes, con campos como `id`, `firstName`, `lastName`.
  Usamos anotaciones JPA como `@Entity`, `@Id`, `@GeneratedValue`.

- **Repositorio `CustomerRepository`**
  Extiende `CrudRepository<Customer, Long>`.
  Incluye métodos personalizados como `findByLastName(String lastName)` y `findById(long id)`.

- **Clase principal `AccessingDataJpaApplication`**
  Punto de entrada Spring Boot.
  Define un bean `CommandLineRunner` que inserta algunos `Customer`, luego hace consultas (`findAll`, `findById`, `findByLastName`) para demostrar cómo se usan los repositorios.

---

## 👣 Cómo ejecutar

Dependiendo del gestor de construcción:

- Con **Maven**:

  ```bash
  ./mvnw spring-boot:run
  ```

  o construir artefacto:

  ```bash
  ./mvnw clean package
  java -jar target/gs-accessing-data-jpa-0.1.0.jar
  ```

## 🧪 Qué esperar como salida

Cuando corras la aplicación, deberías ver algo como:

```
== Customers found with findAll():
Customer[id=1, firstName='Jack', lastName='Bauer']
Customer[id=2, firstName='Chloe', lastName='O'Brian']
Customer[id=3, firstName='Kim', lastName='Bauer']
Customer[id=4, firstName='David', lastName='Palmer']
Customer[id=5, firstName='Michelle', lastName='Dessler']

== Customer found with findById(1L):
Customer[id=1, firstName='Jack', lastName='Bauer']

== Customer found with findByLastName('Bauer'):
Customer[id=1, firstName='Jack', lastName='Bauer']
Customer[id=3, firstName='Kim', lastName='Bauer']
```

---

## ✅ Resumen

Este proyecto demuestra cómo:

- Definir entidades JPA simples.
- Crear repositorios que Spring Data genera automáticamente.
- Realizar operaciones CRUD básicas: guardar, buscar todos, buscar por ID, buscar por atributo.
