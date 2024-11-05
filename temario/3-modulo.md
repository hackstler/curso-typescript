Aquí tienes el temario completo para el **Módulo 3: Tipos Avanzados y Funciones Genéricas** con explicaciones detalladas para que puedas transmitir los conceptos a tus alumnos y comentarios en el código para cada línea, ayudando a entender el propósito de cada instrucción y su utilidad.

---

### **23. Introducción a los Tipos Genéricos** (15 min)

**Objetivo:** Introducir los tipos genéricos y cómo permiten crear funciones y estructuras de datos más flexibles y reutilizables en TypeScript.

**Explicación para los alumnos:**
Los tipos genéricos en TypeScript permiten que nuestras funciones, clases e interfaces trabajen con múltiples tipos sin especificar uno solo. Esto mejora la reutilización y nos da un código más versátil. Los genéricos usan una "variable de tipo" (usualmente `T`) que representa un tipo cualquiera, que luego se define cuando usamos el código.

**Ejemplo de Código:**

```typescript
// Definimos una función genérica que toma un argumento de tipo T y devuelve un valor de tipo T.
function identity<T>(arg: T): T {
  // Simplemente retornamos el mismo argumento que recibimos.
  return arg;
}

// Al llamar a la función, especificamos el tipo genérico. Aquí usamos un número.
console.log(identity<number>(5)); // Imprime: 5

// Ahora, la misma función puede trabajar con un string sin modificar su implementación.
console.log(identity<string>("Hello")); // Imprime: "Hello"
```

---

### **24. Funciones Genéricas y Limitaciones** (15 min)

**Objetivo:** Mostrar cómo crear funciones con múltiples genéricos y explicar las limitaciones de los genéricos.

**Explicación para los alumnos:**
Las funciones genéricas pueden aceptar múltiples tipos, permitiéndonos usarlas en varias combinaciones de tipos sin duplicar código. Sin embargo, los genéricos no pueden inferir ciertos tipos o propiedades a menos que se les añadan restricciones.

**Ejemplo de Código:**

```typescript
// Función genérica con dos parámetros de tipo, T y U.
function pair<T, U>(first: T, second: U): [T, U] {
  // Retornamos una tupla que contiene los dos elementos de tipos T y U.
  return [first, second];
}

// Usamos la función con un string y un número como argumentos.
const result = pair<string, number>("Edad", 25);
console.log(result); // Imprime: ["Edad", 25]
```

---

### **25. Constraints en Genéricos** (15 min)

**Objetivo:** Explicar cómo usar restricciones en los genéricos para asegurar que cumplan ciertos requisitos.

**Explicación para los alumnos:**
A veces necesitamos que un tipo genérico cumpla con ciertas propiedades. Con `extends`, podemos limitar los genéricos para que solo acepten tipos que tengan propiedades específicas, asegurando que nuestra función o clase trabajará como esperamos.

**Ejemplo de Código:**

```typescript
// Definimos una función genérica que solo acepta objetos con una propiedad `name` de tipo string.
function logProperty<T extends { name: string }>(obj: T): void {
  // Accedemos a la propiedad `name` sin error, porque sabemos que el tipo T tiene una propiedad `name`.
  console.log(obj.name);
}

// Llamamos a la función con un objeto que cumple la restricción.
logProperty({ name: "Alice", age: 30 }); // Imprime: "Alice"

// Este código generaría un error, ya que el objeto no tiene la propiedad `name`.
// logProperty({ age: 30 });
```

---

### **26. Type Guards y Narrowing en Genéricos** (15 min)

**Objetivo:** Enseñar cómo aplicar Type Guards y Narrowing en funciones genéricas para manejar los tipos de manera segura.

**Explicación para los alumnos:**
En TypeScript, podemos verificar el tipo de un valor en tiempo de ejecución usando "Type Guards". Esto es particularmente útil en funciones genéricas, donde queremos asegurar que el valor es de un tipo específico antes de aplicarle métodos o propiedades.

**Ejemplo de Código:**

```typescript
// Definimos una función que verifica si el valor recibido es de tipo string.
function isString(value: any): value is string {
  return typeof value === "string";
}

// Función genérica que procesa un valor de cualquier tipo.
function processValue<T>(value: T) {
  // Usamos el Type Guard para verificar si el valor es un string.
  if (isString(value)) {
    // Si es un string, llamamos a un método específico de strings.
    console.log("Valor de tipo string:", value.toUpperCase());
  } else {
    // Si no es un string, lo tratamos como un valor genérico.
    console.log("Otro tipo de valor:", value);
  }
}

// Llamamos a la función con diferentes tipos de valores.
processValue("Hello"); // Imprime: "Valor de tipo string: HELLO"
processValue(123); // Imprime: "Otro tipo de valor: 123"
```

---

### **27. Mapped Types** (15 min)

**Objetivo:** Explicar los Mapped Types, que nos permiten crear nuevos tipos a partir de propiedades de un tipo existente.

**Explicación para los alumnos:**
Los Mapped Types nos permiten transformar las propiedades de un tipo de forma dinámica. Esto es útil cuando queremos generar nuevas versiones de un tipo, como hacer todas sus propiedades opcionales o convertirlas en solo lectura.

**Ejemplo de Código:**

```typescript
// Definimos una interfaz que representa a un usuario.
interface User {
  id: number;
  name: string;
  age: number;
}

// Usamos un Mapped Type para crear una versión parcial del tipo User, donde todas las propiedades son opcionales.
type PartialUser = {
  [P in keyof User]?: User[P];
};

// Ahora podemos crear un objeto que solo contenga algunas propiedades de User.
const user: PartialUser = { name: "Alice" };
```

---

### **28. Tipos Condicionales** (15 min)

**Objetivo:** Introducir los tipos condicionales para crear tipos dinámicos basados en condiciones.

**Explicación para los alumnos:**
Los tipos condicionales son una poderosa herramienta que nos permite definir tipos dependiendo de si una condición se cumple. Esto permite crear tipos complejos y adaptativos en función de otros tipos.

**Ejemplo de Código:**

```typescript
// Definimos un tipo condicional que verifica si T es de tipo string.
type IsString<T> = T extends string ? "Sí" : "No";

// Testeamos el tipo condicional con diferentes tipos.
type Test1 = IsString<string>; // "Sí"
type Test2 = IsString<number>; // "No"
```

---

### **29. Inferencia en Tipos Avanzados** (15 min)

**Objetivo:** Explicar el uso de `infer` en tipos condicionales para extraer tipos dentro de una expresión.

**Explicación para los alumnos:**
La palabra clave `infer` en TypeScript nos permite inferir tipos dentro de una expresión condicional, facilitando la extracción de tipos específicos de una función o clase para reutilizarlos en otras partes.

**Ejemplo de Código:**

```typescript
// Definimos un tipo que infiere el tipo de retorno de una función.
type ReturnType<T> = T extends (...args: any[]) => infer R ? R : never;

// Definimos una función para probar el tipo.
function exampleFunction(): string {
  return "hello";
}

// Usamos el tipo para extraer el tipo de retorno de la función.
type Result = ReturnType<typeof exampleFunction>; // Result será de tipo string
```

---

### **30. Utility Types en TypeScript** (15 min)

**Objetivo:** Introducir los Utility Types de TypeScript, que nos ofrecen herramientas comunes para manipular tipos de manera rápida.

**Explicación para los alumnos:**
TypeScript incluye varios Utility Types, como `Partial`, `Readonly`, `Pick`, y `Omit`, que nos permiten manipular tipos de forma práctica y efectiva, sin tener que definirlos manualmente.

**Ejemplo de Código:**

```typescript
// Definimos una interfaz de ejemplo.
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}

// Usamos el tipo Utility `Partial` para hacer que todas las propiedades sean opcionales.
const todo: Partial<Todo> = { title: "Learn TypeScript" };
```

---

### **31. Utility Types Avanzados** (15 min)

**Objetivo:** Mostrar el uso de Utility Types avanzados, como `Record` y `Required`.

**Explicación para los alumnos:**
Además de los Utility Types básicos, TypeScript incluye otros como `Record`, que facilita la creación de objetos con claves y valores definidos, y `Required`, que convierte todas las propiedades opcionales en requeridas.

**Ejemplo de Código:**

```typescript
// Usamos el tipo `Record` para definir un objeto con claves fijas y valores específicos.
type Page = "home" | "about" | "contact";
type PageInfo = Record<Page, { title: string }>;

const pages: PageInfo = {
  home: { title: "Página Principal" },
  about: { title: "Sobre Nosotros" },
  contact: { title: "Contacto" },
};
```

---

### **32. Aplicación de Utility Types en Funciones** (15 min)

**Objetivo:** Explicar cómo aplicar Utility Types en parámetros de funciones para manipular tipos en la práctica.

**Explicación para los alumnos:**
Los Utility Types pueden

simplificar el manejo de tipos complejos dentro de funciones, especialmente cuando trabajamos con parámetros opcionales o queremos asegurar que ciertas propiedades estén presentes.

**Ejemplo de Código:**

```typescript
interface User {
  id: number;
  name: string;
  age?: number;
}

// Usamos `Required` para asegurar que todas las propiedades de User estén presentes en esta función.
function getUserInfo(user: Required<User>) {
  return `${user.name}, Edad: ${user.age}`;
}

const user: Required<User> = { id: 1, name: "Alice", age: 25 };
console.log(getUserInfo(user)); // Imprime: "Alice, Edad: 25"
```

---

### **33. Refactorización usando Mapped Types** (15 min)

**Objetivo:** Usar mapped types para mejorar la estructura del código.

**Explicación para los alumnos:**
Refactorizar con mapped types permite hacer que nuestro código sea más flexible y adaptable. Aquí mostramos cómo adaptar tipos a partir de tipos existentes para crear estructuras con propiedades modificadas.

**Ejemplo de Código:**

```typescript
// Creamos un tipo ApiResponse que convierte cada propiedad de T en una versión opcional.
type ApiResponse<T> = {
  [P in keyof T]?: T[P] | null;
};

interface User {
  id: number;
  name: string;
}

// Ahora, ApiResponse<User> permite que cada propiedad sea opcional o nula.
const userResponse: ApiResponse<User> = {
  id: 1,
  name: null,
};
```

---

Este módulo cubre todos los conceptos avanzados relacionados con tipos genéricos y manipulación avanzada de tipos en TypeScript. Estas explicaciones te permitirán presentar cada tema con claridad y dar ejemplos detallados a los estudiantes durante los videos.
