Aquí tienes el plan detallado y el código comentado para cada video del **Módulo 1: Introducción a TypeScript y Fundamentos Básicos**. Cada video está estructurado para durar aproximadamente 15 minutos y se enfoca en un tema específico. Además, incluyo comentarios detallados en el código y explicaciones paso a paso para que puedas grabar los videos fácilmente.

---

### **1. Introducción a TypeScript y Configuración** (15 min)

**Objetivo:** Explicar qué es TypeScript, sus ventajas sobre JavaScript y cómo configurar el entorno para empezar a programar en TypeScript.

**Estructura:**

1. **¿Qué es TypeScript?**

   - Explica brevemente la evolución de JavaScript y el surgimiento de TypeScript como un superconjunto que añade tipado estático y mejores herramientas de desarrollo.

2. **Instalación de Node.js y TypeScript**

   - Explica cómo instalar Node.js y TypeScript de forma global.

   ```bash
   # Instalación de TypeScript de manera global
   npm install -g typescript
   ```

3. **Inicialización de un proyecto TypeScript**

   - Muestra cómo crear una carpeta de proyecto y cómo inicializarlo.

   ```bash
   # Crear una carpeta para el proyecto y navegar hasta ella
   mkdir my-first-typescript-project
   cd my-first-typescript-project

   # Inicializar TypeScript
   tsc --init
   ```

4. **Explicación del archivo `tsconfig.json`**

   - Recorre algunas configuraciones clave del archivo `tsconfig.json`, como `target`, `strict`, y `outDir`.

5. **Compilación de un archivo TypeScript**

   - Crea un archivo `index.ts`, añade un pequeño código y compílalo con `tsc`.

   ```typescript
   // index.ts
   let message: string = "Hello, TypeScript!";
   console.log(message);
   ```

   - Explica cómo compilarlo.

   ```bash
   tsc index.ts
   ```

---

### **2. Sintaxis Básica y Variables** (15 min)

**Objetivo:** Presentar la sintaxis básica de TypeScript y cómo declarar variables usando tipos.

**Estructura:**

1. **Declaración de Variables y Tipos Básicos**

   - Explica `string`, `number`, `boolean`, y `any`.

   ```typescript
   let username: string = "Juan";
   let age: number = 30;
   let isActive: boolean = true;
   let anything: any = "Puede ser cualquier cosa";
   ```

2. **Constantes**

   - Explica cómo usar `const` para valores inmutables.

   ```typescript
   const company: string = "My Company";
   ```

3. **Inferencia de Tipos**

   - Muestra cómo TypeScript infiere tipos automáticamente.

   ```typescript
   let inferredType = "This is a string"; // inferredType es de tipo string
   ```

4. **Comentarios en el Código**

   - Explica la importancia de documentar el código usando comentarios.

   ```typescript
   // Esto es un comentario en TypeScript
   ```

---

### **3. Tipado en Funciones y Parámetros** (15 min)

**Objetivo:** Explicar cómo definir funciones con tipos y cómo declarar los tipos de parámetros y retorno.

**Estructura:**

1. **Definición de Funciones y Tipos de Parámetros**

   ```typescript
   function greet(name: string): string {
     return `Hello, ${name}!`;
   }
   ```

2. **Parámetros Opcionales**

   - Explica cómo hacer que un parámetro sea opcional usando `?`.

   ```typescript
   function greetOptional(name?: string): string {
     return `Hello, ${name || "stranger"}!`;
   }
   ```

3. **Tipos de Retorno**

   - Muestra cómo definir tipos específicos para el valor de retorno de una función.

   ```typescript
   function sum(a: number, b: number): number {
     return a + b;
   }
   ```

4. **Funciones Anónimas y Arrow Functions**

   - Explica cómo usar funciones anónimas y arrow functions.

   ```typescript
   const multiply = (x: number, y: number): number => x * y;
   ```

---

### **4. Objetos y Arrays** (15 min)

**Objetivo:** Explicar cómo declarar y tipar objetos y arrays en TypeScript.

**Estructura:**

1. **Objetos**

   - Explica cómo definir objetos y sus propiedades.

   ```typescript
   let person: { name: string; age: number } = {
     name: "Alice",
     age: 25,
   };
   ```

2. **Arrays**

   - Muestra cómo tipar arrays de diferentes tipos.

   ```typescript
   let numbers: number[] = [1, 2, 3, 4];
   let names: string[] = ["Alice", "Bob", "Charlie"];
   ```

3. **Arrays de Objetos**

   ```typescript
   let people: { name: string; age: number }[] = [
     { name: "Alice", age: 25 },
     { name: "Bob", age: 30 },
   ];
   ```

4. **Métodos Array con TypeScript**
   - Muestra algunos métodos de array (`push`, `filter`, etc.).

---

### **5. Interfaces y Type Aliases** (15 min)

**Objetivo:** Introducir interfaces y alias de tipo para una tipificación más estructurada.

**Estructura:**

1. **Interfaces Básicas**

   - Explica cómo definir interfaces.

   ```typescript
   interface Person {
     name: string;
     age: number;
   }

   let user: Person = { name: "John", age: 25 };
   ```

2. **Alias de Tipos (Type Aliases)**

   ```typescript
   type ID = string | number;
   let userId: ID = 101;
   ```

3. **Extensión de Interfaces**

   ```typescript
   interface Employee extends Person {
     role: string;
   }

   let employee: Employee = { name: "Alice", age: 30, role: "Developer" };
   ```

---

### **6. Narrowing y Type Guards** (15 min)

**Objetivo:** Explicar el uso de técnicas de "narrowing" para restringir tipos y los "type guards" en TypeScript.

**Estructura:**

1. **Introducción al Narrowing**

   - Muestra cómo TypeScript "reduce" tipos en condiciones.

   ```typescript
   function printId(id: ID) {
     if (typeof id === "string") {
       console.log("ID es un string:", id.toUpperCase());
     } else {
       console.log("ID es un número:", id);
     }
   }
   ```

2. **Type Guards Personalizados**

   - Explica cómo definir funciones que actúan como "type guards".

   ```typescript
   function isString(value: any): value is string {
     return typeof value === "string";
   }
   ```

---

### **7. Tipos Unión y Alias Avanzados** (15 min)

**Objetivo:** Explicar el uso avanzado de tipos unión y alias de tipos para hacer el código más flexible.

**Estructura:**

1. **Tipos Unión Avanzados**

   ```typescript
   type Response =
     | { success: true; data: string }
     | { success: false; error: string };
   ```

2. **Tipos Literal y Enums**

   ```typescript
   type Status = "success" | "error" | "pending";
   let currentStatus: Status = "pending";
   ```

---

### **8. Práctica de Fundamentos Básicos** (15 min)

**Objetivo:** Repasar los temas cubiertos en el módulo a través de ejercicios prácticos y código interactivo.

**Estructura:**

1. **Creación de una función que use varios de los conceptos cubiertos**

   - Practicar combinando tipos, funciones y arrays.

   ```typescript
   interface Product {
     id: number;
     name: string;
     price: number;
   }

   const products: Product[] = [
     { id: 1, name: "Laptop", price: 1000 },
     { id: 2, name: "Phone", price: 500 },
   ];

   function getProductNames(items: Product[]): string[] {
     return items.map((item) => item.name);
   }

   console.log(getProductNames(products));
   ```

2. **Revisión y Prueba de los Conceptos**
   - Repasar ejemplos clave y animar a la audiencia a modificar los valores para ver los errores de tipo en TypeScript.

---

Este temario abarca todos los temas clave para una introducción sólida a TypeScript y sus fundamentos básicos. ¡Sigue este guion detallado y estarás listo para grabar!
