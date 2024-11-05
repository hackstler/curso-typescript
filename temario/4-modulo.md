Aquí tienes los guiones detallados para el **Módulo 4: Proyecto Completo con TypeScript**. En este módulo, nos enfocaremos en la creación de una aplicación práctica y completa usando los conocimientos adquiridos hasta ahora. Este proyecto integrará varios conceptos avanzados de TypeScript, lo que permitirá reforzar los conocimientos de una forma aplicada.

---

## **Módulo 4: Proyecto Completo con TypeScript (22 Videos - 5.5 horas)**

Cada video está pensado para durar **15 minutos**.

---

### **Video 37: Introducción al Proyecto Completo** (15 min)

**Objetivo**: Presentar el proyecto completo, sus objetivos y la estructura general que se implementará.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "En este módulo, construiremos una aplicación completa usando TypeScript. El proyecto consistirá en una API para gestionar un sistema de inventario de productos."

2. **Descripción del Proyecto** (3 min)

   - Explicar que el proyecto es una API REST para gestionar productos y categorías, donde se podrán agregar, actualizar y eliminar productos, y consultar su inventario.
   - Listar las funcionalidades principales que se desarrollarán:
     - CRUD de productos
     - CRUD de categorías
     - Validación de datos
     - Manejo de errores

3. **Tecnologías y Librerías** (3 min)

   - Presentar las tecnologías y librerías que se utilizarán, como Node.js, Express y MongoDB (o cualquier base de datos en caso de cambios).
   - Explicar la importancia de TypeScript en este contexto para la seguridad y el mantenimiento del código.

4. **Estructura del Proyecto** (4 min)

   - Explicar la estructura de carpetas que se utilizará en el proyecto:
     - `/src`: Carpeta principal del código fuente
     - `/src/models`: Modelos de datos
     - `/src/controllers`: Lógica de controladores para manejar las solicitudes
     - `/src/routes`: Rutas para cada recurso
     - `/src/utils`: Funciones de utilidad

5. **Instalación y Configuración Inicial** (3 min)

   - Crear el proyecto inicial con `npm init` y configurar TypeScript.
   - Instalar las dependencias principales: Express, TypeScript, y Nodemon.

6. **Resumen y Conclusión** (1 min)
   - Resumir los objetivos del proyecto y explicar que en los próximos videos se empezará a construir cada componente de la API.

**Consejo de Grabación**: Explica de forma clara la estructura del proyecto y los objetivos para que los estudiantes comprendan la visión general antes de adentrarse en el código.

---

### **Video 38: Estructura de la API y Configuración Básica** (15 min)

**Objetivo**: Configurar la estructura base de la API con TypeScript y Express, y asegurar que el servidor esté funcionando.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy configuraremos la estructura base de la API y aseguraremos que el servidor Express esté en funcionamiento."

2. **Instalación de Express y Configuración de TypeScript** (3 min)

   - Instalar Express y configurar TypeScript para que compile el código en `/dist`.
   - Configurar `tsconfig.json` para incluir `esModuleInterop`, `outDir`, y otras opciones básicas.

3. **Crear el Servidor Básico con Express** (4 min)

   - Configurar un archivo `index.ts` como punto de entrada de la API y crear un servidor Express básico.
   - Configurar un endpoint `/status` para verificar que el servidor está en funcionamiento.

4. **Instalar y Configurar Nodemon** (3 min)

   - Instalar y configurar Nodemon junto con `ts-node` para la ejecución automática del servidor en modo de desarrollo.
   - Crear un script en `package.json` para iniciar el servidor:
     ```json
     "scripts": {
       "start:dev": "nodemon src/index.ts"
     }
     ```

5. **Verificación del Servidor** (2 min)

   - Ejecutar el servidor y hacer una solicitud a `/status` para confirmar que el servidor responde correctamente.

6. **Resumen y Conclusión** (2 min)
   - Resumir la configuración inicial y explicar que en el siguiente video se empezará a construir la funcionalidad de rutas y controladores.

**Consejo de Grabación**: Mantén el terminal y el editor visibles para que los estudiantes puedan ver cada comando y configuración aplicada en tiempo real.

---

### **Video 39: Configuración de Rutas** (15 min)

**Objetivo**: Configurar las rutas principales de la API, creando los archivos necesarios para organizar las rutas de productos y categorías.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy configuraremos las rutas principales de la API y estableceremos la estructura para manejar los endpoints de productos y categorías."

2. **Crear Archivo de Rutas para Productos** (4 min)

   - Crear un archivo `productos.routes.ts` en la carpeta `routes`.
   - Configurar una ruta básica para listar productos y un endpoint `/productos` con una respuesta de prueba:

     ```typescript
     import { Router } from "express";
     const router = Router();

     router.get("/productos", (req, res) => {
       res.send("Lista de productos");
     });

     export default router;
     ```

3. **Crear Archivo de Rutas para Categorías** (4 min)

   - Repetir el proceso para crear `categorias.routes.ts` con un endpoint de prueba para `/categorias`.

4. **Configurar Rutas en el Servidor Principal** (3 min)

   - Importar ambas rutas en `index.ts` y usarlas en la aplicación Express:

     ```typescript
     import productosRouter from "./routes/productos.routes";
     import categoriasRouter from "./routes/categorias.routes";

     app.use("/api", productosRouter);
     app.use("/api", categoriasRouter);
     ```

5. **Prueba de Rutas Configuradas** (2 min)

   - Ejecutar el servidor y verificar que las rutas de prueba están funcionando correctamente.

6. **Resumen y Conclusión** (1 min)
   - Resumir la estructura de las rutas y anticipar la implementación de controladores en el próximo video.

**Consejo de Grabación**: Usa el navegador o herramientas como Postman para mostrar que los endpoints están respondiendo y que la estructura de rutas está funcionando.

---

### **Video 40: Controladores y Servicios** (15 min)

**Objetivo**: Implementar los controladores de productos y categorías para manejar la lógica de negocio.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy vamos a implementar los controladores para los productos y categorías, donde pondremos la lógica de negocio de la API."

2. **Crear el Controlador de Productos** (4 min)

   - Crear un archivo `productos.controller.ts` en la carpeta `controllers`.
   - Implementar funciones básicas como `obtenerProductos`, `crearProducto`, y `eliminarProducto` con respuestas de prueba.

3. **Crear el Controlador de Categorías** (4 min)

   - Repetir el proceso para crear `categorias.controller.ts` y añadir funciones `obtenerCategorias`, `crearCategoria`, y `eliminarCategoria`.

4. **Conectar Controladores con Rutas** (3 min)

   - Importar los controladores en los archivos de rutas y usar las funciones en los endpoints:
     ```typescript
     router.get("/productos", obtenerProductos);
     router.post("/productos", crearProducto);
     ```

5. **Prueba de los Controladores** (2 min)

   - Ejecutar el servidor y verificar que los controladores devuelven las respuestas esperadas.

6. **Resumen y Conclusión** (1 min)
   - Resumir la organización de controladores y cómo están conectados con las rutas.

**Consejo de Grabación**: Usa ejemplos claros y refuerza la importancia de separar la lógica en controladores para mantener el código organizado y modular.

---

### **Video 41: Validación de Datos** (15 min)

**Objetivo**: Añadir validación de datos en los controladores para asegurar que solo se reciban datos válidos en los endpoints.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy implementaremos validaciones de datos en los controladores para asegurar que solo se reciban datos correctos en nuestros endpoints."

2. **Instalar Librería de Validación** (2 min)

   - Instalar una librería de validación como `joi` para gestionar las reglas de validación.
   - Importar `joi` en `productos.controller.ts` y `categorias.controller.ts`.

3. **Crear Esquema de Validación para Productos** (4 min)

   - Definir un esquema de validación en el controlador de productos usando `joi`:
     ```typescript
     const esquemaProducto = Joi.object({
       nombre: Joi.string().required(),
       precio: Joi.number().required(),
     });
     ```

4. **Aplicar Validación en el Endpoint de Creación** (3 min)

   - Usar el esquema en el método `crearProducto` para validar los datos antes de guardarlos:
     ```typescript
     const { error } = esquemaProducto.validate(req.body);
     if (error) return res.status(400).send(error.details);
     ```

5. \*\*Pruebas de Validación de

Datos\*\* (3 min)

- Probar el endpoint con datos válidos e inválidos para ver cómo responde el servidor a las diferentes solicitudes.

6. **Resumen y Conclusión** (2 min)
   - Resumir la importancia de la validación de datos para asegurar que solo se almacenen datos válidos en la base de datos.

**Consejo de Grabación**: Usa una herramienta como Postman para mostrar cómo los datos válidos e inválidos producen diferentes respuestas del servidor, destacando el papel de las validaciones.

---

Aquí tienes los guiones detallados para el **Módulo 4: Proyecto Completo con TypeScript**. En este módulo, nos enfocaremos en la creación de una aplicación práctica y completa usando los conocimientos adquiridos hasta ahora. Este proyecto integrará varios conceptos avanzados de TypeScript, lo que permitirá reforzar los conocimientos de una forma aplicada.

---

## **Módulo 4: Proyecto Completo con TypeScript (22 Videos - 5.5 horas)**

Cada video está pensado para durar **15 minutos**.

---

### **Video 37: Introducción al Proyecto Completo** (15 min)

**Objetivo**: Presentar el proyecto completo, sus objetivos y la estructura general que se implementará.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "En este módulo, construiremos una aplicación completa usando TypeScript. El proyecto consistirá en una API para gestionar un sistema de inventario de productos."

2. **Descripción del Proyecto** (3 min)

   - Explicar que el proyecto es una API REST para gestionar productos y categorías, donde se podrán agregar, actualizar y eliminar productos, y consultar su inventario.
   - Listar las funcionalidades principales que se desarrollarán:
     - CRUD de productos
     - CRUD de categorías
     - Validación de datos
     - Manejo de errores

3. **Tecnologías y Librerías** (3 min)

   - Presentar las tecnologías y librerías que se utilizarán, como Node.js, Express y MongoDB (o cualquier base de datos en caso de cambios).
   - Explicar la importancia de TypeScript en este contexto para la seguridad y el mantenimiento del código.

4. **Estructura del Proyecto** (4 min)

   - Explicar la estructura de carpetas que se utilizará en el proyecto:
     - `/src`: Carpeta principal del código fuente
     - `/src/models`: Modelos de datos
     - `/src/controllers`: Lógica de controladores para manejar las solicitudes
     - `/src/routes`: Rutas para cada recurso
     - `/src/utils`: Funciones de utilidad

5. **Instalación y Configuración Inicial** (3 min)

   - Crear el proyecto inicial con `npm init` y configurar TypeScript.
   - Instalar las dependencias principales: Express, TypeScript, y Nodemon.

6. **Resumen y Conclusión** (1 min)
   - Resumir los objetivos del proyecto y explicar que en los próximos videos se empezará a construir cada componente de la API.

**Consejo de Grabación**: Explica de forma clara la estructura del proyecto y los objetivos para que los estudiantes comprendan la visión general antes de adentrarse en el código.

---

### **Video 38: Estructura de la API y Configuración Básica** (15 min)

**Objetivo**: Configurar la estructura base de la API con TypeScript y Express, y asegurar que el servidor esté funcionando.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy configuraremos la estructura base de la API y aseguraremos que el servidor Express esté en funcionamiento."

2. **Instalación de Express y Configuración de TypeScript** (3 min)

   - Instalar Express y configurar TypeScript para que compile el código en `/dist`.
   - Configurar `tsconfig.json` para incluir `esModuleInterop`, `outDir`, y otras opciones básicas.

3. **Crear el Servidor Básico con Express** (4 min)

   - Configurar un archivo `index.ts` como punto de entrada de la API y crear un servidor Express básico.
   - Configurar un endpoint `/status` para verificar que el servidor está en funcionamiento.

4. **Instalar y Configurar Nodemon** (3 min)

   - Instalar y configurar Nodemon junto con `ts-node` para la ejecución automática del servidor en modo de desarrollo.
   - Crear un script en `package.json` para iniciar el servidor:
     ```json
     "scripts": {
       "start:dev": "nodemon src/index.ts"
     }
     ```

5. **Verificación del Servidor** (2 min)

   - Ejecutar el servidor y hacer una solicitud a `/status` para confirmar que el servidor responde correctamente.

6. **Resumen y Conclusión** (2 min)
   - Resumir la configuración inicial y explicar que en el siguiente video se empezará a construir la funcionalidad de rutas y controladores.

**Consejo de Grabación**: Mantén el terminal y el editor visibles para que los estudiantes puedan ver cada comando y configuración aplicada en tiempo real.

---

### **Video 39: Configuración de Rutas** (15 min)

**Objetivo**: Configurar las rutas principales de la API, creando los archivos necesarios para organizar las rutas de productos y categorías.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy configuraremos las rutas principales de la API y estableceremos la estructura para manejar los endpoints de productos y categorías."

2. **Crear Archivo de Rutas para Productos** (4 min)

   - Crear un archivo `productos.routes.ts` en la carpeta `routes`.
   - Configurar una ruta básica para listar productos y un endpoint `/productos` con una respuesta de prueba:

     ```typescript
     import { Router } from "express";
     const router = Router();

     router.get("/productos", (req, res) => {
       res.send("Lista de productos");
     });

     export default router;
     ```

3. **Crear Archivo de Rutas para Categorías** (4 min)

   - Repetir el proceso para crear `categorias.routes.ts` con un endpoint de prueba para `/categorias`.

4. **Configurar Rutas en el Servidor Principal** (3 min)

   - Importar ambas rutas en `index.ts` y usarlas en la aplicación Express:

     ```typescript
     import productosRouter from "./routes/productos.routes";
     import categoriasRouter from "./routes/categorias.routes";

     app.use("/api", productosRouter);
     app.use("/api", categoriasRouter);
     ```

5. **Prueba de Rutas Configuradas** (2 min)

   - Ejecutar el servidor y verificar que las rutas de prueba están funcionando correctamente.

6. **Resumen y Conclusión** (1 min)
   - Resumir la estructura de las rutas y anticipar la implementación de controladores en el próximo video.

**Consejo de Grabación**: Usa el navegador o herramientas como Postman para mostrar que los endpoints están respondiendo y que la estructura de rutas está funcionando.

---

### **Video 40: Controladores y Servicios** (15 min)

**Objetivo**: Implementar los controladores de productos y categorías para manejar la lógica de negocio.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy vamos a implementar los controladores para los productos y categorías, donde pondremos la lógica de negocio de la API."

2. **Crear el Controlador de Productos** (4 min)

   - Crear un archivo `productos.controller.ts` en la carpeta `controllers`.
   - Implementar funciones básicas como `obtenerProductos`, `crearProducto`, y `eliminarProducto` con respuestas de prueba.

3. **Crear el Controlador de Categorías** (4 min)

   - Repetir el proceso para crear `categorias.controller.ts` y añadir funciones `obtenerCategorias`, `crearCategoria`, y `eliminarCategoria`.

4. **Conectar Controladores con Rutas** (3 min)

   - Importar los controladores en los archivos de rutas y usar las funciones en los endpoints:
     ```typescript
     router.get("/productos", obtenerProductos);
     router.post("/productos", crearProducto);
     ```

5. **Prueba de los Controladores** (2 min)

   - Ejecutar el servidor y verificar que los controladores devuelven las respuestas esperadas.

6. **Resumen y Conclusión** (1 min)
   - Resumir la organización de controladores y cómo están conectados con las rutas.

**Consejo de Grabación**: Usa ejemplos claros y refuerza la importancia de separar la lógica en controladores para mantener el código organizado y modular.

---

### **Video 41: Validación de Datos** (15 min)

**Objetivo**: Añadir validación de datos en los controladores para asegurar que solo se reciban datos válidos en los endpoints.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy implementaremos validaciones de datos en los controladores para asegurar que solo se reciban datos correctos en nuestros endpoints."

2. **Instalar Librería de Validación** (2 min)

   - Instalar una librería de validación como `joi` para gestionar las reglas de validación.
   - Importar `joi` en `productos.controller.ts` y `categorias.controller.ts`.

3. **Crear Esquema de Validación para Productos** (4 min)

   - Definir un esquema de validación en el controlador de productos usando `joi`:
     ```typescript
     const esquemaProducto = Joi.object({
       nombre: Joi.string().required(),
       precio: Joi.number().required(),
     });
     ```

4. **Aplicar Validación en el Endpoint de Creación** (3 min)

   - Usar el esquema en el método `crearProducto` para validar los datos antes de guardarlos:
     ```typescript
     const { error } = esquemaProducto.validate(req.body);
     if (error) return res.status(400).send(error.details);
     ```

5. \*\*Pruebas de Validación de

Datos\*\* (3 min)

- Probar el endpoint con datos válidos e inválidos para ver cómo responde el servidor a las diferentes solicitudes.

6. **Resumen y Conclusión** (2 min)
   - Resumir la importancia de la validación de datos para asegurar que solo se almacenen datos válidos en la base de datos.

**Consejo de Grabación**: Usa una herramienta como Postman para mostrar cómo los datos válidos e inválidos producen diferentes respuestas del servidor, destacando el papel de las validaciones.

---

Continuaré con los guiones detallados para los siguientes videos del **Módulo 4: Proyecto Completo con TypeScript**. En esta fase, implementaremos funcionalidades avanzadas como middleware, autenticación, pruebas, y optimización del código.

---

Continuaré con los guiones detallados para los siguientes videos del **Módulo 4: Proyecto Completo con TypeScript**. En esta sección, avanzaremos en la implementación del CRUD, manejo de errores y conexión a una base de datos.

---

### **Video 42: Manejo de Errores** (15 min)

**Objetivo**: Implementar un manejo de errores centralizado para la API, asegurando que los errores se gestionen de manera uniforme y clara.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy aprenderemos a implementar un manejo de errores centralizado para nuestra API, lo que nos ayudará a gestionar cualquier error de forma consistente."

2. **Crear Middleware de Manejo de Errores** (4 min)

   - Explicar la necesidad de centralizar el manejo de errores en un middleware.
   - Crear un middleware `manejoErrores.ts` en la carpeta `middleware`:

     ```typescript
     import { Request, Response, NextFunction } from "express";

     export function manejarErrores(
       err: Error,
       req: Request,
       res: Response,
       next: NextFunction
     ) {
       console.error(err.message);
       res.status(500).json({ error: "Ocurrió un error en el servidor" });
     }
     ```

3. **Integrar el Middleware de Errores en el Servidor** (3 min)

   - Importar y usar el middleware `manejarErrores` en el servidor principal (`index.ts`), después de las rutas:
     ```typescript
     import { manejarErrores } from "./middleware/manejoErrores";
     app.use(manejarErrores);
     ```

4. **Modificar Controladores para Usar el Manejo de Errores** (3 min)

   - Actualizar controladores para capturar errores y pasarlos al middleware usando `next`:
     ```typescript
     router.get("/productos", async (req, res, next) => {
       try {
         // lógica
       } catch (error) {
         next(error);
       }
     });
     ```

5. **Pruebas de Errores en Rutas** (2 min)

   - Probar un error intencional en un controlador para verificar que el middleware maneja y muestra el error correctamente.

6. **Resumen y Conclusión** (2 min)
   - Resumir cómo el manejo de errores centralizado mejora la robustez y claridad en la respuesta de errores de la API.

**Consejo de Grabación**: Muestra cómo el middleware captura y formatea los errores, permitiendo una respuesta unificada y fácil de depurar.

---

### **Video 43: Conexión a una Base de Datos** (15 min)

**Objetivo**: Configurar la conexión de la API a una base de datos (MongoDB) usando Mongoose, y asegurar que el servidor se conecte exitosamente.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy conectaremos nuestra API a una base de datos para que los datos de productos y categorías se almacenen y persistan en MongoDB."

2. **Instalación y Configuración de Mongoose** (3 min)

   - Instalar Mongoose usando `npm install mongoose`.
   - Configurar la conexión en un archivo `db.ts` en la carpeta `config`:

     ```typescript
     import mongoose from "mongoose";

     export function conectarDB() {
       mongoose.connect("mongodb://localhost:27017/inventario", {
         useNewUrlParser: true,
         useUnifiedTopology: true,
       });
       mongoose.connection.on("connected", () => {
         console.log("Conectado a la base de datos");
       });
     }
     ```

3. **Integrar la Conexión en el Servidor Principal** (3 min)

   - Llamar a `conectarDB` en `index.ts` antes de iniciar el servidor:
     ```typescript
     import { conectarDB } from "./config/db";
     conectarDB();
     ```

4. **Pruebas de Conexión** (3 min)

   - Ejecutar el servidor y verificar que la conexión a la base de datos sea exitosa.
   - Comprobar los mensajes de la consola para asegurar que Mongoose se conectó correctamente.

5. **Manejo de Errores de Conexión** (3 min)

   - Añadir un mensaje de error en caso de que la conexión a la base de datos falle, capturando eventos de error:
     ```typescript
     mongoose.connection.on("error", (error) => {
       console.error("Error en la conexión a la base de datos:", error);
     });
     ```

6. **Resumen y Conclusión** (2 min)
   - Resumir el proceso de conexión a la base de datos y la importancia de verificar la conexión.

**Consejo de Grabación**: Explica paso a paso cómo configurar la conexión y enfatiza la importancia de manejar errores de conexión.

---

### **Video 44: Creación de Modelos con TypeScript** (15 min)

**Objetivo**: Crear modelos de datos usando Mongoose y TypeScript para definir la estructura de productos y categorías.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy crearemos modelos de datos en nuestra API usando Mongoose y TypeScript para definir la estructura de productos y categorías."

2. **Definir el Modelo de Producto** (5 min)

   - Crear un archivo `producto.model.ts` en la carpeta `models`.
   - Definir el esquema de `Producto` usando Mongoose y TypeScript, y definir los campos básicos:

     ```typescript
     import mongoose, { Schema, Document } from "mongoose";

     interface IProducto extends Document {
       nombre: string;
       precio: number;
       categoria: string;
     }

     const ProductoSchema = new Schema({
       nombre: { type: String, required: true },
       precio: { type: Number, required: true },
       categoria: { type: String, required: true },
     });

     export const Producto = mongoose.model<IProducto>(
       "Producto",
       ProductoSchema
     );
     ```

3. **Definir el Modelo de Categoría** (4 min)

   - Crear un archivo `categoria.model.ts` en `models` y definir el esquema de `Categoria` con campos `nombre` y `descripcion`.

4. **Utilizar Interfaces para Tipado de Modelos** (3 min)

   - Explicar la importancia de las interfaces (`IProducto`, `ICategoria`) para mantener el tipado en TypeScript y asegurar que los modelos cumplan con los tipos.

5. **Prueba de los Modelos en un Endpoint** (2 min)

   - Probar el modelo `Producto` en un controlador de prueba para verificar que se puede crear y guardar un nuevo producto.

6. **Resumen y Conclusión** (2 min)
   - Resumir la creación de modelos y cómo TypeScript ayuda a mantener el control de tipos en la base de datos.

**Consejo de Grabación**: Explica la relación entre los esquemas de Mongoose y las interfaces de TypeScript, mostrando cómo el tipado fuerte asegura que los datos cumplen con las especificaciones.

---

### **Video 45: Operaciones CRUD Básicas** (15 min)

**Objetivo**: Implementar las operaciones CRUD para productos, permitiendo crear, leer, actualizar y eliminar productos en la base de datos.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy implementaremos las operaciones CRUD para productos, lo que permitirá crear, leer, actualizar y eliminar productos en la base de datos."

2. **Crear un Producto** (4 min)

   - Implementar el método `crearProducto` en el controlador de productos para agregar un producto a la base de datos:
     ```typescript
     export const crearProducto = async (req: Request, res: Response) => {
       const nuevoProducto = new Producto(req.body);
       await nuevoProducto.save();
       res.status(201).json(nuevoProducto);
     };
     ```

3. **Leer Productos** (3 min)

   - Implementar `obtenerProductos` para obtener todos los productos de la base de datos y devolverlos como JSON.

4. **Actualizar un Producto** (3 min)

   - Crear el método `actualizarProducto` para actualizar un producto específico usando su ID:
     ```typescript
     export const actualizarProducto = async (req: Request, res: Response) => {
       const productoActualizado = await Producto.findByIdAndUpdate(
         req.params.id,
         req.body,
         { new: true }
       );
       res.json(productoActualizado);
     };
     ```

5. **Eliminar un Producto** (3 min)

   - Implementar `eliminarProducto` para eliminar un producto de la base de datos usando su ID.

6. **Resumen y Conclusión** (1 min)
   - Resumir las operaciones CRUD y su importancia en el manejo de datos en la API.

**Consejo de Grabación**: Usa una herramienta como Postman para demostrar cada operación CRUD, mostrando cómo los cambios se reflejan en la base de datos.

---

### **Video 46: Creación de Endpoints Avanzados** (15 min)

**Objetivo**: Implementar endpoints avanzados, como búsqueda y filtrado de productos por categorías y rango de precio.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy implementaremos endpoints avanzados para búsqueda y filtrado de productos, lo que permitirá a los usuarios encontrar productos por diferentes criterios."

2. **Crear Endpoint de Búsqueda por Nombre** (3 min

)

- Crear un endpoint en el controlador para buscar productos por nombre usando una expresión regular.

3. **Filtrado por Categoría** (4 min)

   - Crear un endpoint de búsqueda que permita filtrar productos por categoría:
     ```typescript
     router.get("/productos/categoria/:categoria", async (req, res) => {
       const productos = await Producto.find({
         categoria: req.params.categoria,
       });
       res.json(productos);
     });
     ```

4. **Filtrado por Rango de Precio** (4 min)

   - Crear un endpoint que acepte un rango de precios y devuelva productos dentro de ese rango.

5. **Pruebas de los Endpoints** (2 min)

   - Probar cada uno de los endpoints usando Postman para asegurarse de que funcionan correctamente y devuelven los resultados esperados.

6. **Resumen y Conclusión** (1 min)
   - Resumir los beneficios de los endpoints avanzados para mejorar la funcionalidad de la API.

**Consejo de Grabación**: Muestra cómo usar filtros y parámetros en la URL para recuperar productos específicos y resalta cómo esto mejora la experiencia del usuario.

---

### **Video 47: Implementación de Middleware** (15 min)

**Objetivo**: Crear e integrar middleware personalizado para tareas como logging, autorización, y validación adicional.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy implementaremos middleware personalizado en nuestra API para manejar tareas comunes como logging y autorización."

2. **Middleware de Logging** (4 min)

   - Crear un middleware `logging.ts` que registre cada solicitud entrante:

     ```typescript
     import { Request, Response, NextFunction } from "express";

     export function logRequest(
       req: Request,
       res: Response,
       next: NextFunction
     ) {
       console.log(`${req.method} ${req.url}`);
       next();
     }
     ```

3. **Configurar el Middleware de Logging** (2 min)

   - Integrar `logRequest` en el servidor principal (`index.ts`) para que se ejecute en cada solicitud:
     ```typescript
     import { logRequest } from "./middleware/logging";
     app.use(logRequest);
     ```

4. **Middleware de Autorización Básica** (5 min)

   - Crear un middleware `autorizacion.ts` que verifique si la solicitud contiene un token de autorización:
     ```typescript
     export function verificarToken(
       req: Request,
       res: Response,
       next: NextFunction
     ) {
       const token = req.headers.authorization;
       if (!token) return res.status(403).json({ error: "Acceso denegado" });
       next();
     }
     ```
   - Explicar cómo este middleware podría ampliarse para validar el token.

5. **Aplicación del Middleware en Rutas Específicas** (2 min)

   - Aplicar `verificarToken` en rutas específicas para protegerlas de accesos no autorizados.

6. **Resumen y Conclusión** (1 min)
   - Resumir la utilidad de los middleware para centralizar tareas comunes y mejorar la seguridad de la API.

**Consejo de Grabación**: Muestra ejemplos de cómo el middleware de logging registra cada solicitud y cómo la autorización bloquea el acceso sin un token válido.

---

### **Video 48: Autenticación y Autorización** (15 min)

**Objetivo**: Implementar autenticación básica en la API usando JWT (JSON Web Token) para proteger rutas y recursos.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy implementaremos autenticación en nuestra API usando JWT para asegurar que solo usuarios autorizados puedan acceder a ciertos recursos."

2. **Instalación de JWT** (2 min)

   - Instalar `jsonwebtoken` y `@types/jsonwebtoken` para manejar tokens:
     ```bash
     npm install jsonwebtoken
     npm install @types/jsonwebtoken -D
     ```

3. **Generación de Tokens de Autenticación** (5 min)

   - Crear un controlador `auth.controller.ts` con un método para generar un token:

     ```typescript
     import jwt from "jsonwebtoken";

     export function login(req: Request, res: Response) {
       const token = jwt.sign({ userId: 123 }, "secreto", { expiresIn: "1h" });
       res.json({ token });
     }
     ```

4. **Verificación de Tokens en Middleware** (3 min)

   - Modificar el middleware `verificarToken` para validar el token usando `jwt.verify`:
     ```typescript
     jwt.verify(token, "secreto", (err, decoded) => {
       if (err) return res.status(403).json({ error: "Token inválido" });
       next();
     });
     ```

5. **Aplicación de Autenticación en Rutas Protegidas** (3 min)

   - Configurar el middleware de autenticación en rutas críticas como creación y eliminación de productos.

6. **Resumen y Conclusión** (1 min)
   - Resumir la implementación de autenticación y cómo los tokens permiten controlar el acceso a recursos.

**Consejo de Grabación**: Explica el proceso de autenticación paso a paso y muestra cómo las rutas protegidas requieren un token válido para funcionar.

---

### **Video 49: Pruebas Unitarias de Componentes** (15 min)

**Objetivo**: Introducir las pruebas unitarias para los controladores, asegurando que las funciones individuales funcionen correctamente.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy implementaremos pruebas unitarias en nuestra API para verificar que los controladores y sus métodos funcionen correctamente."

2. **Instalación de Jest** (2 min)

   - Instalar `jest` y `@types/jest` para manejar pruebas en TypeScript:
     ```bash
     npm install jest ts-jest @types/jest -D
     ```

3. **Configuración de Jest para TypeScript** (3 min)

   - Crear una configuración de Jest (`jest.config.js`) e inicializar `ts-jest`:
     ```typescript
     module.exports = {
       preset: "ts-jest",
       testEnvironment: "node",
     };
     ```

4. **Crear Prueba Unitaria para un Controlador** (5 min)

   - Crear una prueba para el controlador `obtenerProductos` usando Jest:
     ```typescript
     test("obtenerProductos devuelve lista de productos", async () => {
       const req = {} as Request;
       const res = { json: jest.fn() } as unknown as Response;
       await obtenerProductos(req, res);
       expect(res.json).toHaveBeenCalled();
     });
     ```

5. **Ejecutar Pruebas y Ver Resultados** (2 min)

   - Ejecutar Jest y mostrar los resultados de la prueba en la terminal.

6. **Resumen y Conclusión** (2 min)
   - Resumir la importancia de las pruebas unitarias para verificar la funcionalidad básica de cada componente.

**Consejo de Grabación**: Explica cada paso del proceso de configuración y pruebas, mostrando cómo Jest simplifica la ejecución de pruebas unitarias.

---

### **Video 50: Pruebas de Integración** (15 min)

**Objetivo**: Implementar pruebas de integración en la API para verificar que diferentes partes del sistema trabajen en conjunto de manera adecuada.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy vamos a implementar pruebas de integración en nuestra API para asegurar que diferentes partes del sistema trabajen juntas sin problemas."

2. **Concepto de Pruebas de Integración** (2 min)

   - Explicar que las pruebas de integración verifican que varios componentes (como rutas y controladores) trabajen correctamente juntos.

3. **Configurar un Entorno de Pruebas** (3 min)

   - Crear una base de datos temporal o un mock para realizar pruebas sin afectar los datos reales.

4. **Prueba de Integración para una Ruta CRUD** (5 min)

   - Crear una prueba para la ruta de creación de productos (`POST /productos`):
     ```typescript
     test("POST /productos crea un nuevo producto", async () => {
       const response = await request(app)
         .post("/api/productos")
         .send({ nombre: "Producto Test", precio: 10 });
       expect(response.status).toBe(201);
       expect(response.body.nombre).toBe("Producto Test");
     });
     ```

5. **Prueba de Integración para la Ruta de Eliminación** (3 min)

   - Añadir una prueba para verificar que la eliminación de productos funciona correctamente en conjunto con la base de datos.

6. **Resumen y Conclusión** (1 min)
   - Resumir la importancia de las pruebas de integración para validar el flujo completo de datos en la API.

**Consejo de Grabación**: Muestra cómo cada prueba verifica que los controladores y la base de datos funcionen en conjunto, destacando la robustez de la API.

---

### **Video 51: Optimización de Código en la API** (15 min)

**Objetivo**: Revisar el código de la API y aplicar optimizaciones para mejorar la eficiencia y claridad.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy revisaremos y optimizaremos el código de nuestra API para mejorar su eficiencia y claridad."

2. **Refactorización de Controladores** (4 min)

   - Identificar áreas de repetición en los controladores y extraer lógica común a funciones auxiliares.

3. **Optimización de Consultas a la Base de Datos** (4 min)

   - Revisar las consultas a la base de datos para asegurarse de que son eficientes, aplicando `lean()` en búsquedas donde no se necesita la funcionalidad completa de los documentos.

4. **Uso de TypeScript para Prevenir Errores** (3 min)

   - Asegurar que todos los tipos están definidos correctamente, y añadir tipos donde falten para reforzar la seguridad del código.

5. **Minimizar Middleware y Dependencias Innecesarias** (2 min)

   - Revisar el middleware y eliminar dependencias no utilizadas para reducir la carga en la aplicación.

6. **Resumen y Conclusión** (1 min)
   - Resumir cómo las optimizaciones mejoran el rendimiento y la claridad del código en la API.

**Consejo de Grabación**: Explica cada refactorización paso a paso

y muestra cómo los cambios mejoran la eficiencia y mantienen el código limpio.

---

### **Video 52: Implementación de Relaciones entre Modelos** (15 min)

**Objetivo**: Implementar relaciones entre modelos, permitiendo que los productos estén asociados a categorías.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy aprenderemos a implementar relaciones entre modelos en nuestra API para asociar productos a categorías."

2. **Modificar el Modelo de Producto para Incluir Referencia a Categoría** (4 min)

   - Actualizar el esquema de `Producto` para incluir una referencia al modelo `Categoria`:
     ```typescript
     categoria: { type: Schema.Types.ObjectId, ref: "Categoria" }
     ```

3. **Popular Relaciones en Consultas** (4 min)

   - Explicar cómo usar `populate` para cargar datos de la categoría asociada al producto en una consulta:
     ```typescript
     Producto.find().populate("categoria");
     ```

4. **Agregar Controlador para Crear Producto con Categoría** (4 min)

   - Modificar el controlador de creación de producto para aceptar un ID de categoría y asociarlo al nuevo producto.

5. **Prueba de la Relación entre Productos y Categorías** (2 min)

   - Crear un producto que esté asociado a una categoría y verificar que la relación funciona al consultar el producto.

6. **Resumen y Conclusión** (1 min)
   - Resumir la implementación de relaciones y cómo esta funcionalidad amplía las capacidades de la API.

**Consejo de Grabación**: Muestra ejemplos en los que los productos y categorías están conectados, destacando cómo las relaciones simplifican el acceso a datos relacionados.

---

Aquí tienes la continuación de los guiones detallados para el **Módulo 4: Proyecto Completo con TypeScript**. En esta última fase del módulo, abordaremos temas como la integración continua, testing automatizado, la configuración para producción y el despliegue.

---

### **Video 53: Refactorización de Componentes** (15 min)

**Objetivo**: Aplicar refactorización a los componentes clave de la API para mejorar la claridad, reducir duplicación y hacer que el código sea más escalable.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy nos enfocaremos en la refactorización de componentes clave de la API para mejorar la claridad y escalabilidad del código."

2. **Revisión de Código para Duplicación y Complejidad** (3 min)

   - Revisar los controladores y modelos para identificar partes duplicadas o con lógica compleja.
   - Explicar la importancia de reducir la duplicación y mejorar la legibilidad.

3. **Refactorización de Controladores con Funciones Auxiliares** (4 min)

   - Crear funciones auxiliares en un archivo `utils.ts` para lógica repetida, como formateo de respuestas o validación adicional.
   - Ejemplo de función para enviar respuestas de éxito:
     ```typescript
     export function enviarRespuesta(
       res: Response,
       data: any,
       mensaje = "Operación exitosa"
     ) {
       res.json({ mensaje, data });
     }
     ```

4. **Uso de TypeScript para Refactorizar Tipos** (3 min)

   - Refactorizar y organizar los tipos en archivos de `types` o `interfaces` en vez de tenerlos dispersos por los controladores.

5. **Revisión y Limpieza de Dependencias Innecesarias** (2 min)

   - Eliminar paquetes o dependencias no utilizadas y actualizar versiones si es necesario.

6. **Resumen y Conclusión** (2 min)
   - Resumir cómo la refactorización ayuda a mantener el código limpio, organizado y fácil de mantener.

**Consejo de Grabación**: Muestra cómo las funciones auxiliares y la centralización de tipos en TypeScript facilitan la gestión y reutilización del código.

---

### **Video 54: Integración Continua y Testing Automatizado** (15 min)

**Objetivo**: Configurar integración continua (CI) con GitHub Actions para ejecutar pruebas automáticas en cada commit y asegurar la calidad del código.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy configuraremos integración continua (CI) con GitHub Actions para ejecutar pruebas automáticas en cada commit."

2. **Concepto de Integración Continua (CI)** (2 min)

   - Explicar brevemente qué es la integración continua y cómo ayuda a detectar errores temprano en el ciclo de desarrollo.

3. **Configurar GitHub Actions** (3 min)

   - Crear un archivo de flujo de trabajo en `.github/workflows/ci.yml`:

     ```yaml
     name: CI

     on: [push, pull_request]

     jobs:
       build:
         runs-on: ubuntu-latest
         steps:
           - uses: actions/checkout@v2
           - uses: actions/setup-node@v2
             with:
               node-version: "14"
           - run: npm install
           - run: npm test
     ```

4. **Agregar Pruebas en el Flujo de CI** (3 min)

   - Asegurarse de que el comando `npm test` ejecute todas las pruebas, y hacer un commit para ver cómo GitHub Actions ejecuta las pruebas automáticamente.

5. **Verificación de Resultados de CI en GitHub** (3 min)

   - Verificar en la pestaña de acciones de GitHub que las pruebas se ejecutan y se completan correctamente.

6. **Resumen y Conclusión** (2 min)
   - Resumir los beneficios de la CI y cómo la ejecución automática de pruebas asegura la calidad del código.

**Consejo de Grabación**: Explica claramente cada sección del archivo de configuración de GitHub Actions y muestra cómo los resultados de CI aparecen en GitHub.

---

### **Video 55: Configuración de TypeScript para Producción** (15 min)

**Objetivo**: Configurar TypeScript para un entorno de producción, optimizando la API para su despliegue.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy configuraremos TypeScript para producción, asegurando que la API esté optimizada y lista para ser desplegada."

2. **Revisión de Opciones en `tsconfig.json`** (4 min)

   - Ajustar opciones como `strict`, `noEmitOnError`, y `removeComments` en `tsconfig.json` para optimizar el código en producción:
     ```json
     "compilerOptions": {
       "outDir": "./dist",
       "removeComments": true,
       "noEmitOnError": true
     }
     ```

3. **Generación de Archivos Compilados** (3 min)

   - Compilar el proyecto usando `tsc` para generar el código JavaScript optimizado en la carpeta `dist`.

4. **Configuración de Scripts de Producción en `package.json`** (3 min)

   - Añadir un script `start` para producción que use los archivos compilados en `dist`:
     ```json
     "scripts": {
       "build": "tsc",
       "start": "node dist/index.js"
     }
     ```

5. **Pruebas de Ejecución en Entorno de Producción** (3 min)

   - Ejecutar `npm run build` y `npm start` para confirmar que la API funciona correctamente con los archivos compilados.

6. **Resumen y Conclusión** (1 min)
   - Resumir los pasos de configuración para producción y cómo estos optimizan la API.

**Consejo de Grabación**: Explica cómo la configuración optimizada de TypeScript permite una ejecución más rápida y segura en producción.

---

### **Video 56: Documentación de la API** (15 min)

**Objetivo**: Crear una documentación básica de la API usando Swagger para facilitar el uso y la comprensión de los endpoints.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy crearemos documentación para nuestra API usando Swagger, lo que facilitará el uso y la comprensión de nuestros endpoints."

2. **Instalación de Swagger** (2 min)

   - Instalar `swagger-ui-express` y `swagger-jsdoc` para documentar la API:
     ```bash
     npm install swagger-ui-express swagger-jsdoc
     ```

3. **Configuración Básica de Swagger** (4 min)

   - Configurar Swagger en `index.ts` para que esté disponible en `/api-docs`:

     ```typescript
     import swaggerUi from "swagger-ui-express";
     import swaggerDocument from "./swagger.json";

     app.use("/api-docs", swaggerUi.serve, swaggerUi.setup(swaggerDocument));
     ```

4. **Definir Documentación de Endpoints** (4 min)

   - Crear un archivo `swagger.json` o usar comentarios JSDoc para definir los endpoints, sus parámetros, y respuestas.

5. **Pruebas de la Documentación** (3 min)

   - Acceder a `/api-docs` en el navegador para ver la documentación generada y verificar que todos los endpoints están documentados.

6. **Resumen y Conclusión** (1 min)
   - Resumir cómo la documentación ayuda a usuarios y desarrolladores a entender y utilizar la API.

**Consejo de Grabación**: Muestra cómo la documentación aparece en Swagger y explica la utilidad de documentar correctamente los endpoints.

---

### **Video 57: Deploy en Entorno de Pruebas** (15 min)

**Objetivo**: Desplegar la API en un entorno de pruebas para verificar que todo funcione correctamente antes de pasar a producción.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy desplegaremos nuestra API en un entorno de pruebas para verificar que todo funcione correctamente antes del despliegue en producción."

2. **Preparación del Entorno de Pruebas** (3 min)

   - Explicar la diferencia entre los entornos de desarrollo, pruebas y producción.
   - Configurar variables de entorno para diferenciar las configuraciones.

3. **Deploy en un Servicio de Pruebas** (4 min)

   - Desplegar la API en un servicio de pruebas como Heroku o Render, configurando las variables de entorno necesarias.

4. **Configuración de la Base de Datos de Pruebas** (3 min)

   - Conectar la API a una base de datos de pruebas en MongoDB Atlas u otro servicio en la nube.

5. **Verificación y Pruebas en Entorno de Pruebas** (3 min)

   - Probar los endpoints y funcionalidades en el entorno de pruebas para confirmar que la API funciona como esperado.

6. **Resumen y Conclusión** (1 min)
   - Resumir la importancia de realizar pruebas exhaustivas en un entorno de pruebas antes de pasar a producción.

**Consejo de Grabación**: Muestra cómo configurar el despliegue en el servicio de pruebas y verifica cada endpoint para asegurar que la API funcione correctamente en este entorno.

---

### **Video 58: Monitoreo de la API** (15 min)

**Objetivo**: Configurar herramientas de monitoreo para la API en producción y aprender a rastrear errores

y rendimiento.

**Guion Paso a Paso**:

1. **Introducción al Video** (1 min)

   - "Hoy configuraremos herramientas de monitoreo para nuestra API en producción para poder rastrear errores y mejorar el rendimiento."

2. **Concepto de Monitoreo y su Importancia** (2 min)

   - Explicar la importancia de monitorear una API en producción para identificar problemas y optimizar el rendimiento.

3. **Configuración de Herramientas de Monitoreo** (3 min)

   - Usar servicios como Sentry o LogRocket para monitorear errores y registrar logs en tiempo real.

4. **Configuración de Logging Avanzado** (3 min)

   - Implementar un sistema de logging que registre errores importantes y los envíe a un archivo o servicio externo para revisión.

5. **Pruebas de Monitoreo** (3 min)

   - Forzar un error en la API para confirmar que el servicio de monitoreo lo registra y notifica correctamente.

6. **Resumen y Conclusión** (3 min)
   - Resumir los beneficios del monitoreo en la producción y cómo este proceso ayuda a mantener la estabilidad de la API.

**Consejo de Grabación**: Muestra cómo configurar el monitoreo y destaca cómo las alertas permiten una respuesta rápida a problemas en producción.

---

Con estos videos finales, completamos el **Módulo 4** y el despliegue completo de la API en producción con TypeScript. ¿Te gustaría que comience a estructurar los guiones para el siguiente módulo de **Testing, Configuración y Deployment** en el curso?
