Aquí tienes el temario detallado con explicaciones extensas y comentarios en el código para los videos del **Módulo 5: Testing, Configuración y Deployment**. Este módulo está diseñado para guiar a los estudiantes en la configuración avanzada de TypeScript, pruebas, automatización de testing y despliegue en producción.

---

### **59. Configuración Avanzada de tsconfig.json** (15 min)

**Objetivo:** Explorar configuraciones avanzadas del archivo `tsconfig.json` para optimizar el proyecto.

**Explicación para los alumnos:**
El archivo `tsconfig.json` define cómo TypeScript debe compilar el código. Con configuraciones avanzadas, podemos ajustar el comportamiento de TypeScript para mejorar la compatibilidad y optimizar el rendimiento de la aplicación.

**Ejemplo de Configuración en `tsconfig.json`:**

```json
{
  "compilerOptions": {
    "target": "es6", // Especifica la versión de ECMAScript del código JavaScript resultante
    "module": "commonjs", // Define el sistema de módulos que se usará, aquí 'commonjs' para Node.js
    "strict": true, // Habilita todas las verificaciones estrictas de TypeScript
    "baseUrl": "./src", // Define la ruta base para resolver módulos relativos
    "paths": {
      "@models/*": ["models/*"], // Crea un alias para simplificar importaciones
      "@controllers/*": ["controllers/*"]
    },
    "outDir": "./dist", // Carpeta donde se generará el código compilado
    "sourceMap": true, // Genera mapas de código fuente para facilitar debugging
    "removeComments": true, // Remueve comentarios en el código compilado
    "esModuleInterop": true // Facilita la importación de módulos ES en Node.js
  },
  "include": ["src/**/*"], // Incluye todos los archivos TypeScript en src
  "exclude": ["node_modules", "dist"] // Excluye carpetas innecesarias
}
```

---

### **60. Configuración para Ambientes de Desarrollo y Producción** (15 min)

**Objetivo:** Configurar variables y ajustes para distintos entornos (desarrollo y producción).

**Explicación para los alumnos:**
Configurar diferentes ambientes nos permite ajustar el comportamiento de la API según el entorno (por ejemplo, habilitar `logging` en desarrollo y desactivarlo en producción). Utilizaremos variables de entorno para establecer configuraciones específicas.

**Ejemplo de Configuración de Entorno con `dotenv`:**

```typescript
// Instalación de dotenv para gestionar variables de entorno
npm install dotenv

// src/config.ts
import dotenv from 'dotenv';

// Carga las variables de entorno desde el archivo .env
dotenv.config();

export const config = {
    PORT: process.env.PORT || 3000, // Puerto de la API
    DATABASE_URL: process.env.DATABASE_URL || '', // URL de la base de datos
    NODE_ENV: process.env.NODE_ENV || 'development', // Ambiente actual
    JWT_SECRET: process.env.JWT_SECRET || 'default_secret' // Clave secreta para JWT
};

// src/index.ts
import { config } from './config';

const PORT = config.PORT;
// Configuración del puerto y ambiente
app.listen(PORT, () => {
    console.log(`Servidor en ejecución en modo ${config.NODE_ENV} en http://localhost:${PORT}`);
});
```

---

### **61. Testing en TypeScript con Jest** (15 min)

**Objetivo:** Configurar Jest para TypeScript y realizar pruebas básicas.

**Explicación para los alumnos:**
Jest es un marco de pruebas que permite ejecutar pruebas unitarias e integradas en TypeScript. Configuraremos Jest para TypeScript y realizaremos una prueba inicial para verificar que esté correctamente configurado.

**Instalación de Dependencias y Configuración de Jest:**

```bash
npm install jest ts-jest @types/jest --save-dev
```

**Configurar Jest en `jest.config.js`:**

```javascript
module.exports = {
  preset: "ts-jest", // Usar ts-jest para compilar TypeScript
  testEnvironment: "node", // Define el entorno de pruebas
  moduleNameMapper: {
    "^@models/(.*)$": "<rootDir>/src/models/$1", // Configura alias para Jest
  },
};
```

---

### **62. Pruebas Unitarias con Jest (Parte 1)** (15 min)

**Objetivo:** Crear pruebas unitarias para funciones simples y servicios.

**Explicación para los alumnos:**
Las pruebas unitarias validan que cada componente funcione correctamente de forma aislada. Vamos a escribir pruebas unitarias para nuestras funciones y servicios utilizando Jest, asegurando que cada parte del código cumpla con su propósito.

**Ejemplo de Prueba Unitaria para un Servicio:**

```typescript
// src/services/mathService.ts
export const add = (a: number, b: number): number => a + b;

// src/tests/mathService.test.ts
import { add } from "../services/mathService";

test("Debe sumar dos números correctamente", () => {
  const result = add(3, 4);
  expect(result).toBe(7); // Espera que el resultado sea 7
});
```

---

### **63. Pruebas Unitarias con Jest (Parte 2)** (15 min)

**Objetivo:** Continuar desarrollando pruebas unitarias para casos más complejos.

**Explicación para los alumnos:**
Exploraremos casos más complejos, como la validación de errores y el manejo de valores especiales. Estas pruebas refuerzan la robustez de nuestras funciones y servicios, asegurando que manejen correctamente escenarios variados.

**Ejemplo de Prueba Unitaria con Errores:**

```typescript
// src/services/userService.ts
export const getUserById = (id: string): string | null => {
  if (id === "123") return "User123";
  return null;
};

// src/tests/userService.test.ts
import { getUserById } from "../services/userService";

test("Debe devolver el usuario cuando el ID es válido", () => {
  expect(getUserById("123")).toBe("User123");
});

test("Debe devolver null cuando el ID es inválido", () => {
  expect(getUserById("456")).toBeNull(); // Verifica el caso de error
});
```

---

### **64. Pruebas de Integración con Jest** (15 min)

**Objetivo:** Implementar pruebas de integración para verificar la interacción de varios componentes.

**Explicación para los alumnos:**
Las pruebas de integración aseguran que múltiples componentes funcionen juntos correctamente. Usaremos Jest para crear pruebas que validen la funcionalidad de la API, simulando solicitudes HTTP y verificando las respuestas.

**Ejemplo de Prueba de Integración:**

```typescript
// src/tests/integration/userIntegration.test.ts
import request from "supertest";
import app from "../index";

describe("Pruebas de integración para la API de usuarios", () => {
  it("Debe obtener todos los usuarios", async () => {
    const response = await request(app).get("/api/users");
    expect(response.status).toBe(200);
    expect(Array.isArray(response.body)).toBe(true); // Verifica que la respuesta es un array
  });
});
```

---

### **65. Cobertura de Código y Reportes** (15 min)

**Objetivo:** Configurar cobertura de código para medir la calidad de las pruebas.

**Explicación para los alumnos:**
La cobertura de código mide el porcentaje de código cubierto por pruebas, ayudándonos a identificar áreas sin pruebas. Con Jest, generaremos reportes de cobertura para obtener una visión completa de la calidad de las pruebas.

**Comando para Ejecutar Cobertura de Código con Jest:**

```bash
# Ejecutar pruebas con cobertura
npm test -- --coverage
```

**Reportes Generados:**

- **Statements**: porcentaje de sentencias cubiertas.
- **Branches**: porcentaje de ramificaciones cubiertas.
- **Functions**: porcentaje de funciones cubiertas.
- **Lines**: porcentaje de líneas de código cubiertas.

---

### **66. Automatización de Testing con Scripts** (15 min)

**Objetivo:** Crear scripts para automatizar las pruebas.

**Explicación para los alumnos:**
Automatizar pruebas permite ejecutarlas de forma eficiente antes de cada despliegue. Configuraremos scripts en el `package.json` para ejecutar pruebas unitarias, de integración y de cobertura de forma sencilla.

**Ejemplo de Scripts de Testing en `package.json`:**

```json
"scripts": {
    "test": "jest", // Ejecuta todas las pruebas
    "test:unit": "jest --testPathPattern=src/tests/unit", // Ejecuta solo las pruebas unitarias
    "test:integration": "jest --testPathPattern=src/tests/integration", // Ejecuta solo las pruebas de integración
    "coverage": "jest --coverage" // Genera reporte de cobertura
}
```

---

### **67. Optimización de la Configuración para Tests Rápidos** (15 min)

**Objetivo:** Optimizar la configuración de Jest para que las pruebas se ejecuten rápidamente.

**Explicación para los alumnos:**
Las pruebas rápidas facilitan el desarrollo ágil. Podemos ajustar la configuración de Jest para evitar compilaciones innecesarias y maximizar la eficiencia de las pruebas.

**Ejemplo de Optimización en `jest.config.js`:**

```javascript
module.exports = {
  preset: "ts-jest",
  testEnvironment: "node",
  cacheDirectory: "./cache", // Habilita caché de pruebas para mayor velocidad
  maxWorkers: "50%", // Limita el uso de CPU para evitar sobrecarga
};
```

---

### **68. Configuración de CI/CD con GitHub Actions** (15 min)

**Objetivo:** Configurar un flujo de CI/CD en GitHub Actions.

**Explicación para los alumnos:**
La integración continua permite ejecutar pruebas y asegurarse de que cada cambio en el código funcione correctamente. Configuraremos GitHub Actions para ejecutar las pruebas y generar reportes de cobertura en cada `push` al repositorio.

**Ejemplo de Configuración de CI/CD en GitHub Actions:**

```yaml
# .github/workflows/ci-cd.yml
name: CI/CD Pipeline

on:
  push:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - name: Configurar Node.js
        uses: actions/setup-node@v2
        with:
          node-version: "14"
      - run: npm install
      - run: npm test
```

---

### **69. Deploy Automatizado en Producción** (15 min)

**Objetivo:** Configurar despliegue automatizado en un servicio como Heroku o Vercel.

**Explicación para los alumnos:**
Con CI/CD, podemos automatizar el despliegue del proyecto cada vez que el código en la rama principal pase todas las pruebas. Veremos cómo configurar GitHub Actions para hacer un despliegue automatizado en Heroku.

**Ejemplo de Configuración para Despliegue en Heroku:**

```yaml
# .github/workflows/deploy.yml
name: Deploy to Heroku

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - name: Login en Heroku
        run: echo "$HEROKU_API_KEY" | docker login --username=_ --password-stdin registry.heroku.com
      - name: Construir y Desplegar
        run: |
          heroku container:push web --app=my-heroku-app
          heroku container:release web --app=my-heroku-app
```

---

### **70. Estrategias de Despliegue en la Nube** (15 min)

**Objetivo:** Explorar distintas estrategias de despliegue y sus beneficios.

**Explicación para los alumnos:**
Existen varias estrategias para desplegar aplicaciones en la nube, como `blue-green`, `canary` o `rolling updates`. Cada estrategia tiene ventajas y desventajas en cuanto a minimización de tiempos de inactividad y reducción de riesgos en los despliegues.

**Principales Estrategias de Despliegue:**

1. **Blue-Green Deployment**: Despliega una nueva versión en paralelo y cambia el tráfico a ella gradualmente.
2. **Canary Release**: Libera cambios en etapas, dirigiendo solo un pequeño porcentaje del tráfico a la nueva versión.
3. **Rolling Updates**: Actualiza instancias en lotes, asegurando que siempre haya al menos una instancia antigua funcionando.

---

Este es el temario completo para el **Módulo 5** con explicaciones detalladas y ejemplos de código bien comentados para ayudarte a enseñar a tus alumnos sobre testing, configuración avanzada y despliegue en producción.
