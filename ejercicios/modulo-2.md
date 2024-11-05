Aquí tienes el temario y el código comentado para cada video del **Módulo 2: Programación Orientada a Objetos en TypeScript**. Cada video está diseñado para durar aproximadamente 15 minutos y detalla cada tema clave de POO en TypeScript.

---

### **9. Clases y Objetos** (15 min)

**Objetivo:** Introducir las clases y objetos en TypeScript.

**Estructura:**

1. **Creación de una Clase Básica**

   - Explica cómo declarar una clase y un objeto.

   ```typescript
   class Person {
     name: string;
     age: number;

     constructor(name: string, age: number) {
       this.name = name;
       this.age = age;
     }
   }

   const person1 = new Person("Alice", 30);
   console.log(person1);
   ```

2. **Instanciación de Objetos**
   - Muestra cómo crear múltiples instancias y explica el uso de `new`.

---

### **10. Constructores y Modificadores de Acceso** (15 min)

**Objetivo:** Explicar constructores y modificadores de acceso `public`, `private`, y `protected`.

**Estructura:**

1. **Uso del Constructor**

   - Explica el propósito del constructor en la inicialización de propiedades.

2. **Modificadores de Acceso**

   - Explica `public`, `private`, y `protected`.

   ```typescript
   class Car {
     public brand: string;
     private model: string;
     protected year: number;

     constructor(brand: string, model: string, year: number) {
       this.brand = brand;
       this.model = model;
       this.year = year;
     }
   }
   ```

3. **Acceso a Propiedades Privadas y Protegidas**

---

### **11. Herencia y Extensión de Clases** (15 min)

**Objetivo:** Explicar cómo funciona la herencia en TypeScript.

**Estructura:**

1. **Creación de una Clase Base y una Subclase**

   - Explica `extends` para extender clases.

   ```typescript
   class Animal {
     species: string;

     constructor(species: string) {
       this.species = species;
     }

     makeSound(): void {
       console.log("Some generic sound");
     }
   }

   class Dog extends Animal {
     constructor() {
       super("Dog");
     }

     makeSound(): void {
       console.log("Woof! Woof!");
     }
   }
   ```

---

### **12. Métodos y Propiedades Estáticas** (15 min)

**Objetivo:** Introducir métodos y propiedades estáticas.

**Estructura:**

1. **Definir una Propiedad Estática**

   - Explica la palabra clave `static`.

   ```typescript
   class MathUtils {
     static PI: number = 3.1416;

     static calculateCircumference(diameter: number): number {
       return this.PI * diameter;
     }
   }

   console.log(MathUtils.calculateCircumference(10));
   ```

2. **Uso de Métodos Estáticos**

---

### **13. Abstract Classes e Interfaces Avanzadas** (15 min)

**Objetivo:** Explicar el uso de clases abstractas y su relación con interfaces.

**Estructura:**

1. **Creación de una Clase Abstracta**

   - Explica `abstract` y cómo funciona.

   ```typescript
   abstract class Vehicle {
     abstract move(): void;

     start(): void {
       console.log("Starting engine...");
     }
   }

   class Bike extends Vehicle {
     move(): void {
       console.log("The bike is moving");
     }
   }
   ```

---

### **14. Polimorfismo** (15 min)

**Objetivo:** Introducir el concepto de polimorfismo y cómo aplicarlo.

**Estructura:**

1. **Polimorfismo con Clases y Métodos**

   - Explica cómo las subclases pueden sobrescribir métodos.

   ```typescript
   class Animal {
     makeSound(): void {
       console.log("Some sound");
     }
   }

   class Cat extends Animal {
     makeSound(): void {
       console.log("Meow");
     }
   }

   const animals: Animal[] = [new Animal(), new Cat()];
   animals.forEach((animal) => animal.makeSound());
   ```

---

### **15. Encapsulación y Abstracción** (15 min)

**Objetivo:** Explicar los principios de encapsulación y abstracción.

**Estructura:**

1. **Encapsulación con `private` y `protected`**

   ```typescript
   class BankAccount {
     private balance: number = 0;

     deposit(amount: number): void {
       if (amount > 0) {
         this.balance += amount;
       }
     }

     getBalance(): number {
       return this.balance;
     }
   }
   ```

---

### **16. Interfaces en Clases** (15 min)

**Objetivo:** Explicar el uso de interfaces para definir contratos de clase.

**Estructura:**

1. **Implementación de una Interface en una Clase**

   ```typescript
   interface Drivable {
     drive(): void;
   }

   class Car implements Drivable {
     drive(): void {
       console.log("The car is driving");
     }
   }
   ```

---

### **17. Clases Genéricas** (15 min)

**Objetivo:** Introducir clases genéricas para crear estructuras reutilizables.

**Estructura:**

1. **Creación de una Clase Genérica**

   ```typescript
   class Box<T> {
     content: T;

     constructor(content: T) {
       this.content = content;
     }

     getContent(): T {
       return this.content;
     }
   }

   const numberBox = new Box<number>(123);
   console.log(numberBox.getContent());
   ```

---

### **18. Interfaces Genéricas** (15 min)

**Objetivo:** Explicar interfaces genéricas para permitir flexibilidad en el diseño.

**Estructura:**

1. **Definición de una Interface Genérica**

   ```typescript
   interface Repository<T> {
     add(item: T): void;
     get(id: number): T;
   }

   class UserRepository implements Repository<User> {
     private users: User[] = [];

     add(user: User): void {
       this.users.push(user);
     }

     get(id: number): User {
       return this.users.find((user) => user.id === id)!;
     }
   }
   ```

---

### **19. Práctica con Clases y Objetos** (15 min)

**Objetivo:** Repasar los conceptos anteriores con un ejercicio práctico.

**Estructura:**

1. **Crear una Aplicación Simple con Clases**

   ```typescript
   class Product {
     constructor(
       public id: number,
       public name: string,
       public price: number
     ) {}
   }

   class Store {
     private products: Product[] = [];

     addProduct(product: Product): void {
       this.products.push(product);
     }

     getProductNames(): string[] {
       return this.products.map((p) => p.name);
     }
   }

   const store = new Store();
   store.addProduct(new Product(1, "Laptop", 1500));
   console.log(store.getProductNames());
   ```

---

### **20. Ejemplo Completo con POO (Parte 1)** (15 min)

**Objetivo:** Crear un ejemplo de aplicación con POO.

**Estructura:**

1. **Diseñar una Aplicación con Clases y Relaciones**

   - Explica la arquitectura de una aplicación que usa varias clases relacionadas, como `Customer`, `Order`, y `Product`.

   ```typescript
   class Customer {
     constructor(public id: number, public name: string) {}
   }

   class Product {
     constructor(
       public id: number,
       public name: string,
       public price: number
     ) {}
   }
   ```

---

### **21. Ejemplo Completo con POO (Parte 2)** (15 min)

**Objetivo:** Continuar desarrollando el ejemplo de aplicación.

**Estructura:**

1. **Completar el Diseño de la Aplicación**

   - Implementar métodos que conecten `Customer`, `Order`, y `Product`.

   ```typescript
   class Order {
     constructor(
       public orderId: number,
       public customer: Customer,
       public products: Product[]
     ) {}

     getTotal(): number {
       return this.products.reduce(
         (total, product) => total + product.price,
         0
       );
     }
   }
   ```

---

### **22. Refactorización y Buenas Prácticas en POO** (15 min)

**Objetivo:** Revisar y mejorar el código de la aplicación.

**Estructura:**

1. **Revisión de Buenas Prácticas**

   - Explica principios como el SRP (Principio de Responsabilidad Única) y cómo aplicarlo.

2. **Refactorización del Código**

   ```typescript
   class Customer {
     private orders: Order[] = [];

     addOrder(order: Order): void {
       this.orders.push(order);
     }
   }
   ```

3. **Conclusión de Buenas Prácticas**

---

Este módulo cubre la programación orientada a objetos en profundidad y ofrece ejemplos prácticos para que los conceptos queden claros y estructurados para el video.
