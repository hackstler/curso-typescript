¡Perfecto! Continuaré con el **Módulo 2** siguiendo el mismo nivel de detalle en los guiones para cada video. Esto permitirá que cada video de 15 minutos esté completamente estructurado y facilite su grabación y presentación.

---

## **Módulo 2: Programación Orientada a Objetos en TypeScript (14 Videos - 3.5 horas)**

Cada video está pensado para durar **15 minutos**.

---

### **Video 9: Clases y Objetos** (15 min)

**Objetivo**: Introducir la Programación Orientada a Objetos (POO) en TypeScript, con un enfoque en clases y objetos.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy daremos un paso importante en TypeScript y entraremos en la Programación Orientada a Objetos aprendiendo sobre clases y objetos."

2. **Concepto de Clases en TypeScript** (3 min)

   - Explicar qué es una clase y cómo se relaciona con un objeto.
   - Mencionar que una clase es un modelo o plano de datos y comportamiento.
   - Crear una clase básica `Persona` con propiedades y métodos:

     ```typescript
     class Persona {
       nombre: string;
       edad: number;

       constructor(nombre: string, edad: number) {
         this.nombre = nombre;
         this.edad = edad;
       }

       saludar() {
         console.log(`Hola, soy ${this.nombre} y tengo ${this.edad} años.`);
       }
     }
     ```

3. **Instanciación de Objetos** (3 min)

   - Explicar cómo se crean objetos a partir de una clase con el operador `new`.
   - Crear un objeto `persona1` de la clase `Persona` e invocar su método `saludar`:
     ```typescript
     const persona1 = new Persona("Juan", 30);
     persona1.saludar();
     ```

4. **Propiedades y Métodos en Clases** (3 min)

   - Describir la diferencia entre propiedades (datos) y métodos (funcionalidades).
   - Añadir un método adicional a la clase para mostrar cómo una clase puede encapsular tanto datos como comportamiento.

5. **Modificadores de Acceso** (3 min)

   - Introducir el concepto de modificadores de acceso: `public` y `private`.
   - Explicar que `public` permite el acceso desde fuera de la clase y `private` restringe el acceso.
   - Modificar la propiedad `edad` para que sea privada y crear un método para acceder a ella:

     ```typescript
     class Persona {
       private edad: number;

       constructor(public nombre: string, edad: number) {
         this.edad = edad;
       }

       obtenerEdad() {
         return this.edad;
       }
     }
     ```

6. **Resumen** (2 min)
   - Repasar la estructura de una clase y los conceptos de propiedades, métodos y modificadores de acceso.

**Consejo de Grabación**: Mantén el editor visible en todo momento y explica los cambios en tiempo real, especialmente cuando cambias una propiedad de `public` a `private` para mostrar su efecto.

---

### **Video 10: Constructores y Modificadores de Acceso** (15 min)

**Objetivo**: Profundizar en los constructores de clase y entender los modificadores de acceso (`public`, `private`, `protected`).

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "En este video, exploraremos los constructores de clase y cómo podemos usar modificadores de acceso para controlar el acceso a propiedades y métodos."

2. **Explicación del Constructor** (3 min)

   - Explicar el constructor como un método especial para inicializar objetos.
   - Mostrar un ejemplo de constructor que recibe parámetros y asigna valores a las propiedades.

3. **Sintaxis Simplificada con Modificadores en el Constructor** (3 min)

   - Explicar cómo se pueden declarar propiedades directamente en el constructor usando `public` o `private`.
   - Modificar la clase `Persona` para simplificar la declaración de propiedades:

     ```typescript
     class Persona {
       constructor(public nombre: string, private edad: number) {}

       saludar() {
         console.log(`Hola, soy ${this.nombre}`);
       }
     }
     ```

   - Crear una instancia de `Persona` y explicar cómo el constructor simplificado mantiene la privacidad de `edad`.

4. **Modificador `protected`** (3 min)

   - Introducir el modificador `protected`, explicando que permite el acceso a propiedades y métodos en clases derivadas.
   - Modificar la clase `Persona` para incluir una propiedad `protected` y explicar su utilidad.

5. **Ejemplo Práctico con `private` y `protected`** (3 min)

   - Crear una subclase `Empleado` que extiende `Persona` y accede a la propiedad `protected`.

     ```typescript
     class Empleado extends Persona {
       constructor(nombre: string, edad: number, public puesto: string) {
         super(nombre, edad);
       }

       mostrarInformacion() {
         console.log(`Empleado: ${this.nombre}, puesto: ${this.puesto}`);
       }
     }
     ```

6. **Resumen y Conclusión** (2 min)
   - Recapitular la utilidad de los modificadores de acceso y cómo controlan la visibilidad de propiedades y métodos en una clase.

**Consejo de Grabación**: Usa un ejemplo sencillo que muestre cómo el modificador `protected` permite el acceso en subclases, pero no desde fuera de la clase, y compara con `public` y `private`.

---

### **Video 11: Herencia y Extensión de Clases** (15 min)

**Objetivo**: Explicar el concepto de herencia en TypeScript y cómo extender clases para reutilizar y especializar el comportamiento.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy vamos a aprender sobre la herencia en TypeScript, un principio clave de la Programación Orientada a Objetos."

2. **Concepto de Herencia** (3 min)

   - Explicar el concepto de herencia y cómo permite que una clase derive de otra, reutilizando y extendiendo sus propiedades y métodos.
   - Comparar la herencia con el concepto de "padre e hijo".

3. **Creación de una Subclase** (4 min)

   - Crear una clase `Persona` básica y una subclase `Estudiante` que extiende de `Persona`.

     ```typescript
     class Persona {
       constructor(public nombre: string, public edad: number) {}
     }

     class Estudiante extends Persona {
       constructor(nombre: string, edad: number, public curso: string) {
         super(nombre, edad);
       }
     }
     ```

   - Explicar el uso de `super` para llamar al constructor de la clase base.

4. **Añadir Métodos a la Subclase** (3 min)

   - Añadir un método en `Estudiante` y otro en `Persona` para demostrar cómo la subclase puede extender el comportamiento de la clase base.

     ```typescript
     class Estudiante extends Persona {
       constructor(nombre: string, edad: number, public curso: string) {
         super(nombre, edad);
       }

       mostrarInformacion() {
         console.log(`${this.nombre}, curso: ${this.curso}`);
       }
     }
     ```

5. **Sobrescritura de Métodos** (3 min)

   - Explicar cómo la subclase puede sobrescribir métodos de la clase base para personalizar el comportamiento.
   - Ejemplo en el que `Estudiante` sobrescribe el método `saludar` de `Persona`.

6. **Resumen y Conclusión** (1 min)
   - Repasar el concepto de herencia, `super`, y sobrescritura de métodos.

**Consejo de Grabación**: Usa ejemplos en los que se observe claramente la relación entre la clase base y la subclase, mostrando cómo los métodos de la clase base pueden ser llamados o sobrescritos en la subclase.

---

### **Video 12: Métodos y Propiedades Estáticas** (15 min)

**Objetivo**: Explicar los métodos y propiedades estáticas en TypeScript y cómo se utilizan en el contexto de una clase.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy aprenderemos sobre métodos y propiedades estáticas en TypeScript, que son compartidos por todas las instancias de una clase."

2. **Concepto de Propiedades y Métodos Estáticos** (3 min)

   - Explicar que los métodos y propiedades estáticas pertenecen a la clase, no a las instancias de la clase.
   - Ejemplo simple con una propiedad estática:
     ```typescript
     class Utilidades {
       static PI = 3.1416;
     }
     console.log(Utilidades.PI);
     ```

3. **Definición de Métodos Estáticos** (4 min)

   - Crear un método estático en `Utilidades` para demostrar cómo realizar cálculos sin necesidad de instanciar la clase.
   - Ejemplo de un método estático para calcular el área de un círculo:
     ```typescript
     class Utilidades {
       static calcularAreaCirculo(radio: number): number {
         return Utilidades.PI * radio * radio;
       }
     }
     ```

4. **Diferencia entre Estático y No Estático** (3 min)
   - Comparar un método normal con un método estático

, mostrando cómo el método no estático requiere una instancia, mientras que el estático no.

- Crear una instancia de `Utilidades` para demostrar cómo los métodos no estáticos se comportan de manera distinta.

5. **Uso de Propiedades Estáticas en la Industria** (3 min)

   - Explicar ejemplos comunes, como constantes o valores compartidos que deben ser accesibles desde cualquier lugar del código.
   - Mencionar cómo las propiedades estáticas pueden ser útiles en configuraciones globales.

6. **Resumen y Conclusión** (1 min)
   - Repasar la diferencia entre métodos y propiedades estáticas y su utilidad en TypeScript.

**Consejo de Grabación**: Haz hincapié en que las propiedades y métodos estáticos no requieren instancias, y usa ejemplos prácticos donde sean útiles para valores o funciones de utilidad global.

---

Continuaré detallando los guiones paso a paso para los siguientes videos del **Módulo 2**. Esto permitirá seguir con la estructura clara y organizada para facilitar tanto la grabación como la explicación de cada concepto.

---

### **Video 13: Clases Abstractas e Interfaces Avanzadas** (15 min)

**Objetivo**: Introducir el concepto de clases abstractas y explorar las interfaces avanzadas en TypeScript.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy veremos las clases abstractas y cómo podemos usarlas junto con interfaces avanzadas para diseñar jerarquías de clases en TypeScript."

2. **Concepto de Clases Abstractas** (3 min)

   - Explicar qué es una clase abstracta y por qué se utiliza.
   - Resaltar que no se puede instanciar y que sirve como una plantilla para otras clases.
   - Crear una clase abstracta `Figura` con un método abstracto `calcularArea`.

3. **Implementación de Métodos Abstractos** (3 min)

   - Crear un método abstracto dentro de `Figura` que debe ser implementado por cualquier subclase:
     ```typescript
     abstract class Figura {
       abstract calcularArea(): number;
     }
     ```
   - Explicar que el método abstracto define una interfaz que las subclases deben implementar.

4. **Extensión de Clases Abstractas** (3 min)

   - Crear una clase `Circulo` que extiende `Figura` e implementa el método `calcularArea`.
     ```typescript
     class Circulo extends Figura {
       constructor(public radio: number) {
         super();
       }

       calcularArea(): number {
         return Math.PI * this.radio ** 2;
       }
     }
     ```
   - Instanciar `Circulo` y demostrar el uso de `calcularArea`.

5. **Interfaces Avanzadas** (3 min)

   - Explicar cómo una clase puede implementar múltiples interfaces.
   - Crear una `interface` `Perimetro` que la clase `Circulo` también implementará:

     ```typescript
     interface Perimetro {
       calcularPerimetro(): number;
     }

     class Circulo extends Figura implements Perimetro {
       // Implementar ambos métodos
     }
     ```

6. **Resumen y Conclusión** (2 min)
   - Repasar la utilidad de clases abstractas y interfaces avanzadas para crear estructuras de código escalables y flexibles.

**Consejo de Grabación**: Usa ejemplos visuales para ilustrar cómo las subclases deben implementar métodos abstractos y cómo se combinan interfaces y clases para agregar funcionalidades específicas.

---

### **Video 14: Polimorfismo** (15 min)

**Objetivo**: Explicar el concepto de polimorfismo y su implementación en TypeScript.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy vamos a estudiar el polimorfismo en TypeScript y cómo nos permite tratar diferentes tipos de objetos de manera uniforme."

2. **Concepto de Polimorfismo** (3 min)

   - Explicar qué es el polimorfismo en programación orientada a objetos.
   - Mencionar cómo permite utilizar un método de la misma manera en diferentes clases que implementan el mismo comportamiento.

3. **Implementación de Polimorfismo con Clases** (3 min)

   - Crear una clase `Triangulo` que también extiende de `Figura` e implementa su propia versión de `calcularArea`.
     ```typescript
     class Triangulo extends Figura {
       constructor(public base: number, public altura: number) {
         super();
       }

       calcularArea(): number {
         return (this.base * this.altura) / 2;
       }
     }
     ```

4. **Ejemplo de Uso Polimórfico** (3 min)

   - Crear una función que reciba una lista de objetos de tipo `Figura` y calcule sus áreas.
   - La función debe poder aceptar tanto `Circulo` como `Triangulo` debido a su estructura polimórfica:
     ```typescript
     function calcularAreas(figuras: Figura[]) {
       figuras.forEach((figura) => {
         console.log(figura.calcularArea());
       });
     }
     ```

5. **Polimorfismo y Interfaces** (3 min)

   - Explicar que el polimorfismo también se puede aplicar con interfaces.
   - Modificar el ejemplo para incluir una interfaz que permita calcular el perímetro y extender el polimorfismo a ese comportamiento.

6. **Resumen y Conclusión** (2 min)
   - Resumir la utilidad del polimorfismo y cómo ayuda a construir código flexible y extensible.

**Consejo de Grabación**: Usa una variedad de ejemplos en tiempo real para demostrar cómo los objetos de diferentes clases pueden ser tratados de la misma manera usando polimorfismo.

---

### **Video 15: Encapsulación y Abstracción** (15 min)

**Objetivo**: Explorar los principios de encapsulación y abstracción en TypeScript, dos pilares fundamentales de la POO.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy aprenderemos sobre encapsulación y abstracción, dos conceptos clave para proteger y simplificar nuestro código."

2. **Concepto de Encapsulación** (3 min)

   - Explicar la encapsulación y cómo oculta los detalles internos de una clase.
   - Crear una clase `CuentaBancaria` con propiedades privadas para `saldo` y métodos para interactuar con el saldo:

     ```typescript
     class CuentaBancaria {
       private saldo: number = 0;

       depositar(cantidad: number) {
         this.saldo += cantidad;
       }

       consultarSaldo() {
         return this.saldo;
       }
     }
     ```

3. **Beneficios de la Encapsulación** (3 min)

   - Explicar cómo la encapsulación evita accesos directos a los datos sensibles.
   - Mostrar cómo el usuario de `CuentaBancaria` solo puede interactuar a través de los métodos de la clase.

4. **Concepto de Abstracción** (3 min)

   - Explicar cómo la abstracción permite simplificar el uso de una clase mostrando solo lo necesario.
   - Crear un método adicional en `CuentaBancaria` para transferir fondos y mostrar cómo la abstracción es útil para ocultar la complejidad:

     ```typescript
     class CuentaBancaria {
       //...

       transferir(destino: CuentaBancaria, cantidad: number) {
         if (cantidad <= this.saldo) {
           this.saldo -= cantidad;
           destino.depositar(cantidad);
         }
       }
     }
     ```

5. **Relación entre Encapsulación y Abstracción** (3 min)

   - Explicar que la abstracción define una interfaz simplificada para la clase, mientras que la encapsulación protege sus datos internos.

6. **Resumen y Conclusión** (2 min)
   - Resumir cómo estos principios mejoran la seguridad y mantenibilidad del código.

**Consejo de Grabación**: Enfatiza cómo la encapsulación y la abstracción trabajan juntos, y muestra ejemplos en pantalla donde la encapsulación protege los datos de accesos no deseados.

---

### **Video 16: Interfaces en Clases** (15 min)

**Objetivo**: Comprender cómo utilizar interfaces en TypeScript para definir contratos que las clases deben seguir.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy aprenderemos cómo usar interfaces en TypeScript para definir contratos que aseguran que las clases implementen cierto comportamiento."

2. **Concepto de Interfaces en Clases** (3 min)

   - Explicar qué es una interfaz y cómo actúa como contrato para una clase.
   - Crear una interfaz `Vehiculo` que defina los métodos `acelerar` y `frenar`:
     ```typescript
     interface Vehiculo {
       acelerar(): void;
       frenar(): void;
     }
     ```

3. **Implementación de Interfaces en Clases** (3 min)

   - Crear una clase `Coche` que implemente la interfaz `Vehiculo`:
     ```typescript
     class Coche implements Vehiculo {
       acelerar() {
         console.log("El coche acelera");
       }

       frenar() {
         console.log("El coche frena");
       }
     }
     ```

4. **Ventajas de Usar Interfaces** (3 min)

   - Explicar cómo las interfaces aseguran que las clases implementen el comportamiento necesario.
   - Crear una segunda clase `Moto` que también implemente `Vehiculo` para mostrar cómo ambas clases siguen el mismo contrato.

5. **Polimorfismo con Interfaces** (3 min)

   - Usar una función que acepte cualquier objeto de tipo `Vehiculo` y demuestre cómo las interfaces soportan polimorfismo.
     ```typescript
     function manejarVehiculo(vehiculo: Vehiculo) {
       vehiculo.acelerar();
     }
     ```
   - Pasar instancias de `Coche` y `Moto` a la función `manejarVehiculo` para mostrar el polimorfismo en acción.

6. **Resumen y Conclusión** (2 min)
   - Resumir el uso de interfaces para crear contratos y cómo esto facilita la extensión del comportamiento.

**Consejo de Grabación**: Demuestra cómo una interfaz facilita el polimorfismo al permitir que varias clases implementen el mismo conjunto de métodos.

---

Continuaré con los guiones detallados para los siguientes videos del **Módulo 2**. Esto permitirá que cada concepto de Programación Orientada a Objetos (POO) en TypeScript quede completamente cubierto.

---

### **Video 17: Clases Genéricas** (15 min)

**Objetivo**: Explicar el concepto de clases genéricas en TypeScript y cómo usar parámetros de tipo (`<T>`) para aumentar la flexibilidad y reusabilidad de las clases.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy aprenderemos sobre las clases genéricas, una herramienta que permite que nuestras clases sean flexibles y reutilizables al trabajar con diferentes tipos de datos."

2. **Concepto de Genéricos en Clases** (3 min)

   - Explicar qué es un genérico (`<T>`) y cómo permite que una clase opere sobre distintos tipos de datos.
   - Introducir la sintaxis de `<T>` en TypeScript como un marcador de posición para el tipo de dato.

3. **Ejemplo de Clase Genérica Básica** (3 min)

   - Crear una clase `Caja<T>` que pueda almacenar cualquier tipo de dato en una propiedad `contenido`.
   - Mostrar cómo `T` se convierte en un tipo dinámico que se asigna cuando se crea una instancia de `Caja`:

     ```typescript
     class Caja<T> {
       contenido: T;

       constructor(contenido: T) {
         this.contenido = contenido;
       }

       obtenerContenido(): T {
         return this.contenido;
       }
     }
     ```

4. **Instanciación de Clases Genéricas** (3 min)

   - Crear instancias de `Caja` con diferentes tipos, como `number` y `string`:
     ```typescript
     const cajaNumero = new Caja<number>(123);
     const cajaTexto = new Caja<string>("Hola");
     ```
   - Explicar cómo TypeScript infiere el tipo `T` y ayuda a prevenir errores de tipo.

5. **Aplicación Práctica de Clases Genéricas** (3 min)

   - Mostrar un caso práctico en el que una clase genérica sea útil para manejar un contenedor de elementos de cualquier tipo.
   - Explicar cómo los genéricos eliminan la necesidad de duplicar clases para cada tipo de dato.

6. **Resumen y Conclusión** (2 min)
   - Resumir la importancia de los genéricos para construir clases flexibles y cómo el parámetro `T` permite manejar diferentes tipos de datos en una sola clase.

**Consejo de Grabación**: Resalta en el editor cómo el autocompletado y las verificaciones de tipo de TypeScript funcionan para cada instancia específica de `Caja<T>`, y enfatiza la versatilidad que proporcionan los genéricos.

---

### **Video 18: Interfaces Genéricas** (15 min)

**Objetivo**: Introducir las interfaces genéricas en TypeScript y su uso para definir contratos que acepten diferentes tipos de datos.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy exploraremos las interfaces genéricas en TypeScript, que permiten crear contratos flexibles y adaptables a distintos tipos de datos."

2. **Concepto de Interfaces Genéricas** (3 min)

   - Explicar cómo las interfaces genéricas, igual que las clases genéricas, utilizan un parámetro `<T>` para manejar distintos tipos.
   - Mostrar la sintaxis básica de una interfaz genérica `CajaGenerica<T>`:
     ```typescript
     interface CajaGenerica<T> {
       contenido: T;
       obtenerContenido(): T;
     }
     ```

3. **Implementación de una Interfaz Genérica** (3 min)

   - Crear una clase que implemente `CajaGenerica<T>` para manejar diferentes tipos de contenido:

     ```typescript
     class CajaTexto implements CajaGenerica<string> {
       contenido: string;
       constructor(contenido: string) {
         this.contenido = contenido;
       }

       obtenerContenido() {
         return this.contenido;
       }
     }
     ```

4. **Uso Práctico de Interfaces Genéricas** (3 min)

   - Explicar cómo las interfaces genéricas pueden ser útiles para definir contratos en estructuras como listas o pilas.
   - Ejemplo: Crear una interfaz `Lista<T>` con métodos `agregar` y `obtener` que puedan manejar cualquier tipo de dato:
     ```typescript
     interface Lista<T> {
       agregar(item: T): void;
       obtener(index: number): T;
     }
     ```

5. **Comparación con Clases Genéricas** (3 min)

   - Comparar las interfaces genéricas con las clases genéricas, destacando que las interfaces permiten implementar un contrato de flexibilidad.
   - Explicar cuándo elegir una interfaz genérica sobre una clase genérica, dependiendo del contexto y del diseño de la aplicación.

6. **Resumen y Conclusión** (2 min)
   - Resumir cómo las interfaces genéricas ayudan a definir contratos flexibles y reutilizables en distintos contextos.

**Consejo de Grabación**: Destaca cómo las interfaces genéricas permiten implementar clases con consistencia y seguridad, y muestra cómo TypeScript ayuda a seguir estos contratos.

---

### **Video 19: Práctica con Clases y Objetos** (15 min)

**Objetivo**: Consolidar los conceptos de clases, herencia, modificadores de acceso, y métodos aplicando un ejercicio práctico.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy aplicaremos todo lo que hemos aprendido sobre clases y objetos en un ejercicio práctico para reforzar estos conceptos."

2. **Descripción del Ejercicio** (2 min)

   - Crear una estructura de clases para representar una librería, con clases `Libro` y `Libreria`.
   - Explicar que `Libro` tendrá propiedades como `titulo`, `autor`, `precio`, y un método `mostrarInfo`.

3. **Implementación de la Clase `Libro`** (4 min)

   - Crear la clase `Libro` con las propiedades mencionadas y el método `mostrarInfo`:

     ```typescript
     class Libro {
       constructor(
         public titulo: string,
         public autor: string,
         public precio: number
       ) {}

       mostrarInfo() {
         return `${this.titulo} de ${this.autor}, Precio: $${this.precio}`;
       }
     }
     ```

4. **Creación de la Clase `Libreria`** (3 min)

   - Crear la clase `Libreria` que contendrá una lista de libros y métodos para agregar y listar libros.
   - Agregar un método `listarLibros` que recorra los libros y muestre su información.

5. **Instanciación y Uso de la Librería** (3 min)

   - Instanciar varios objetos `Libro` y agregarlos a la `Libreria`.
   - Ejecutar `listarLibros` para ver el resultado y comprobar que todos los libros se muestran correctamente.

6. **Resumen y Conclusión** (2 min)
   - Recapitular cómo se ha aplicado la creación de clases, herencia y encapsulación en este ejercicio práctico.

**Consejo de Grabación**: Haz pausas para explicar cada paso, asegurándote de que el flujo del ejercicio sea claro y fácil de seguir.

---

### **Video 20: Ejemplo Completo con POO (Parte 1)** (15 min)

**Objetivo**: Comenzar un proyecto completo aplicando principios de Programación Orientada a Objetos en TypeScript, centrado en la estructura de clases y relaciones entre ellas.

**Guion Paso a Paso**:

1. **Introducción al Proyecto** (2 min)

   - "Hoy comenzaremos un proyecto completo usando Programación Orientada a Objetos en TypeScript. Crearemos una aplicación de gestión de empleados."

2. **Descripción de la Estructura del Proyecto** (3 min)

   - Explicar que el proyecto incluirá las clases `Empleado`, `Departamento`, y `Empresa`.
   - Describir brevemente cada clase y su función en la estructura.

3. **Implementación de la Clase `Empleado`** (5 min)

   - Crear la clase `Empleado` con propiedades como `nombre`, `puesto`, `salario`, y un método `mostrarInfo`.
   - Ejemplo:

     ```typescript
     class Empleado {
       constructor(
         public nombre: string,
         public puesto: string,
         public salario: number
       ) {}

       mostrarInfo() {
         console.log(
           `${this.nombre}, ${this.puesto}, Salario: ${this.salario}`
         );
       }
     }
     ```

4. **Implementación de la Clase `Departamento`** (3 min)

   - Crear la clase `Departamento` que contenga una lista de empleados y métodos para agregar y listar empleados.
   - Agregar un método `listarEmpleados` que recorra y muestre la información de cada empleado.

5. **Resumen y Preparación para la Parte 2** (2 min)
   - Resumir los avances en la implementación y explicar que en la próxima sesión se añadirá la clase `Empresa` para completar la estructura.

**Consejo de Grabación**: Mantén la estructura del código clara y organizada, explicando cómo cada clase colabora con las otras para construir la aplicación.

---

### **Video 21: Ejemplo Completo con POO (Parte 2)** (15 min)

**Objetivo**: Completar el proyecto de ejemplo añadiendo la clase `Empresa` y métodos de interacción entre las clases.

**Guion Paso a Paso**:

1. \*\*Introducción y Rep

aso de la Parte 1\*\* (2 min)

- "En la parte anterior creamos las clases `Empleado` y `Departamento`. Hoy completaremos el proyecto añadiendo la clase `Empresa`."

2. **Implementación de la Clase `Empresa`** (5 min)

   - Crear la clase `Empresa` con propiedades `nombre`, `departamentos`, y métodos para agregar departamentos.
   - Mostrar cómo la clase `Empresa` coordina a `Departamento` y `Empleado`.

3. **Métodos de Interacción entre Clases** (4 min)

   - Añadir un método en `Empresa` que recorra todos los departamentos y liste a los empleados.
   - Explicar cómo estos métodos permiten coordinar el flujo de información en la empresa.

4. **Instanciación y Prueba Completa** (3 min)

   - Crear una instancia de `Empresa`, agregarle departamentos y empleados.
   - Ejecutar el método de listado para ver la estructura completa en funcionamiento.

5. **Resumen y Conclusión del Proyecto** (1 min)
   - Resumir cómo se han usado los principios de POO en la construcción de este proyecto y los beneficios de esta estructura en la organización de datos.

**Consejo de Grabación**: Enfatiza cómo los métodos de interacción entre clases ayudan a mantener la aplicación organizada y a aprovechar los beneficios de la POO.

---

### **Video 22: Refactorización y Buenas Prácticas en POO** (15 min)

**Objetivo**: Aplicar técnicas de refactorización y buenas prácticas de POO en TypeScript para mejorar la legibilidad y mantenibilidad del código.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy aprenderemos a refactorizar el código del proyecto de ejemplo para mejorar su legibilidad y cumplir con buenas prácticas de programación orientada a objetos."

2. **Identificación de Mejoras en el Código** (3 min)

   - Revisar el código del proyecto y señalar áreas de mejora, como reducción de duplicación de código o mejor organización de métodos.

3. **Refactorización de Métodos** (3 min)

   - Mover algunos métodos de `Empresa` a `Departamento` para distribuir mejor las responsabilidades.
   - Explicar cómo esto mejora la cohesión de cada clase.

4. **Aplicación de Principios SOLID** (4 min)

   - Aplicar principios de SOLID (por ejemplo, principio de responsabilidad única) para hacer que cada clase tenga una responsabilidad clara.
   - Explicar cómo estos principios aumentan la mantenibilidad del código a largo plazo.

5. **Renombramiento y Estandarización de Nombres** (3 min)

   - Cambiar nombres de métodos y propiedades para hacerlos más claros y descriptivos.
   - Explicar cómo nombres bien elegidos ayudan a otros desarrolladores a entender el código.

6. **Resumen y Conclusión del Módulo** (1 min)
   - Resumir las buenas prácticas aplicadas y su impacto en la calidad del proyecto.

**Consejo de Grabación**: Usa el antes y después de la refactorización para mostrar claramente cómo los cambios mejoran la estructura y la claridad del código.

---
