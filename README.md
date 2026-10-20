# 🟦 TypeScript con Node.js

Introduccion al entorno de TypeScript, se explora la sintaxis, el tipado estático, la compilación a JavaScript y la ejecución sobre Node.js.

---

## 📂 Estructura del Proyecto

```text
.
├── dist/                # Código JavaScript transpilado
│   ├── estudiante.js
│   └── saludo.js
├── src/                 # Código fuente en TypeScript
│   ├── estudiante.ts
│   └── saludo.ts
├── package.json         # Dependencias y scripts
├── tsconfig.json        # Configuración del compilador de TS
└── README.md
```

---

## ⚙️ Configuración del Entorno

Documentación completa para inicializar, configurar, compilar y ejecutar un entorno de desarrollo de TypeScript desde cero.

---

## 1. Inicialización del Proyecto Node.js

Para crear el archivo de configuración `package.json`:

* **Instalación rápida con valores por defecto (Recomendado):**
  El flag `-y` (o `--yes`) omite el cuestionario interactivo y genera un `package.json` de inmediato.
  ```bash
  npm init -y
  ```

* **Instalación interactiva:**
  Si deseas definir manualmente el nombre del proyecto, versión, descripción y autor:
  ```bash
  npm init
  ```

---

## 2. Instalación de Dependencias

Instalamos TypeScript como dependencia de desarrollo usando el flag `-D` (equivalente a `--save-dev`). Esto evita incluir el compilador en el paquete final de producción.

```bash
npm install typescript -D
```

---

## 3. Configuración del Compilador (`tsconfig.json`)

Generamos el archivo de configuración oficial del compilador de TypeScript (`tsc`):

```bash
npx tsc --init
```

Abre `tsconfig.json` y configura los siguientes parámetros para sincronizar las carpetas de origen (`src`) y salida (`dist`):

```json
{
  "compilerOptions": {
    "target": "es2016",                  /* Versión objetivo de JavaScript */
    "module": "commonjs",                /* Sistema de módulos para Node.js */
    "rootDir": "./src",                  /* Directorio de archivos TypeScript (.ts) */
    "outDir": "./dist",                  /* Directorio de archivos compilados (.js) */
    "strict": true,                      /* Activa el modo estricto de comprobación de tipos */
    "esModuleInterop": true,             /* Facilita la importación de módulos CommonJS */
    "skipLibCheck": true,                /* Omite la verificación de tipos en librerías externas */
    "forceConsistentCasingInFileNames": true
  }
}
```

---

## 4. Estructura de Directorios

Crea la carpeta de código fuente `src` donde colocarás tus archivos `.ts`:

```text
.
├── src/                 # Código fuente TypeScript
│   └── archivo.ts
├── dist/                # Código JavaScript transpilado (generado automáticamente)
├── package.json
├── package-lock.json
└── tsconfig.json
```

---

## 5. Automatización en `package.json`

Añade los scripts de compilación y ejecución dentro del bloque `"scripts"` de tu archivo `package.json`:

```json
"scripts": {
  "build": "tsc",
  "start": "node dist/archivo.js",
  "dev": "tsc --watch"
}
```

---

## 6. Compilación y Ejecución

### 🛠️ Compilación (`.ts` ➔ `.js`)

* **Compilar todo el proyecto (Recomendado):**
  Toma la configuración de `tsconfig.json`, procesa todos los archivos dentro de `./src` y genera la salida en `./dist`:
  ```bash
  npx tsc
  ```
  *(También puedes usar el script configurado: `npm run build`)*

* **Compilar un solo archivo en ruta específica:**
  ```bash
  npx tsc src/archivo.ts
  ```

### 🚀 Ejecución

Ejecuta el archivo compilado en JavaScript utilizando Node.js:

```bash
node dist/archivo.js
```
*(También puedes usar el script configurado: `npm start`)*