<div align="center">

  <img src="rolla_logo.png" alt="Rolla Storage Engine Logo" width="140" style="filter: drop-shadow(0 0 20px rgba(132, 204, 22, 0.4)); margin-bottom: 1rem;">

  # 📦 ROLLA STORAGE ENGINE
  ### *Motor de Almacenamiento de Objetos Inmutable e Ilimitado a Coste $0*

  [![npm version](https://img.shields.io/npm/v/terra-rolla.svg?style=for-the-badge&logo=npm&logoColor=white&color=84cc16)](https://www.npmjs.com/package/terra-rolla)
  [![Ecosistema Terra](https://img.shields.io/badge/Ecosistema-Terra-blue?style=for-the-badge&logo=planetScale&logoColor=white)](https://github.com/amglogicalis/Terra)
  [![Consola Web 24/7](https://img.shields.io/badge/Consola%20Web-Desplegada-2ea043?style=for-the-badge&logo=github&logoColor=white)](https://amglogicalis.github.io/rolla-repo-public/)
  [![Licencia MIT](https://img.shields.io/badge/Licencia-MIT-purple?style=for-the-badge)](https://opensource.org/licenses/MIT)

</div>

---

## 📌 Visión General

**Rolla** (`terra-rolla`) es un motor de almacenamiento de objetos inmutable de alto rendimiento (estilo AWS S3) diseñado para el ecosistema **Terra**. Utiliza la infraestructura global de **GitHub Releases & Assets** alojada en la nube de GitHub sobre un repositorio privado (`.rolla-storage`) para ofrecer espacio de almacenamiento ilimitado a **coste $0** sin saturar ramas ni repositorios Git.

---

## 🚀 Instalación Rápida

### 🌐 Instalación Global de la CLI (Terminal):
```bash
npm install -g terra-rolla
```

### 📦 Instalación en Proyectos (SDK TypeScript / JavaScript):
```bash
npm install terra-rolla
```

---

## 📸 Vista Previa de la Consola Web

<div align="center">
  <img src="cap_preview_console_web.PNG" alt="Rolla Web Console Interface Preview" width="100%" style="border-radius: 12px; border: 1px solid rgba(132, 204, 22, 0.3); box-shadow: 0 10px 30px rgba(0,0,0,0.5);">
</div>

---

## 🌟 Características Destacadas

- ♾️ **Coste $0 y Almacenamiento Ilimitado**: Aprovecha la CDN de Releases de GitHub sin cuotas de subida ni suscripciones.
- 📦 **Rolla-Balls (Buckets)**: Mapeadas internamente como Releases firmadas con tags git `rolla-bkt-<nombre>`.
- 🔄 **Versionado Automático de Objetos (v1.1.0)**: Al volver a subir un objeto con el mismo nombre, se guarda un historial inmutable de versiones permitiendo recuperar cualquier versión previa.
- ⚡ **Sincronización Instantánea**: Consulta de tags vía Git Refs (`/git/refs/tags`) eliminando latencias de caché.
- 🧩 **Automatic Chunking (>2 GB)**: División y ensamblado transparente para archivos gigantescos.
- 🌐 **Consola Web Estática (GitHub Pages)**: Interfaz cliente 24/7 totalmente responsive para PC y dispositivos móviles.
- 💻 **CLI & Servidor Local**: Herramienta de consola para terminal y servidor local de desarrollo.
- 🔒 **Seguridad y Privacidad**: Tu token PAT se guarda localmente en tu cliente (`localStorage`), jamás en servidores externos.

---

## 💻 Todos los Comandos del CLI (`rolla`)

La herramienta CLI de **Rolla** permite gestionar tus objetos y lanzar consolas de desarrollo desde cualquier terminal:

| Comando | Descripción | Ejemplo de Uso |
| :--- | :--- | :--- |
| `rolla console` | **Lanza la Consola Web local** en tu navegador (`http://localhost:3000`). | `rolla console` |
| `rolla console --logs` | Lanza la consola web local mostrando en terminal los **logs detallados** de peticiones HTTP, eventos y errores. | `rolla console --logs` |
| `rolla console --port <puerto>` | Especifica un **puerto personalizado** para la consola web en caso de conflicto. | `rolla console --port 8080` |
| `rolla ls` | **Lista todas las Rolla-Balls (buckets)** existentes en tu cuenta. | `rolla ls` |
| `rolla create <ball-name>` | **Crea una nueva Rolla-Ball** en la nube. | `rolla create fotos-2026` |
| `rolla rename <old-name> <new-name>` | **Renombra una Rolla-Ball** existente. | `rolla rename fotos-2026 galeria-2026` |
| `rolla rm <ball-name>` | **Elimina una Rolla-Ball** y todos los objetos contenidos. | `rolla rm fotos-2026` |
| `rolla ls <ball-name>` | **Lista los objetos y archivos** dentro de una Rolla-Ball específica. | `rolla ls fotos-2026` |
| `rolla upload <ball-name> <file-path>` | **Subir un archivo** a la Rolla-Ball especificada. | `rolla upload fotos-2026 ./imagen.png` |
| `rolla rm <ball-name> <key>` | **Elimina un objeto** de una Rolla-Ball. | `rolla rm fotos-2026 imagen.png` |

---

## 🌐 Uso desde la Consola Web Estática (GitHub Pages)

Accede a la Consola Web desplegada 24/7 desde cualquier navegador de ordenador o teléfono móvil:

👉 **[https://amglogicalis.github.io/rolla-repo-public/](https://amglogicalis.github.io/rolla-repo-public/)**

1. Ingresa tu **GitHub Personal Access Token (PAT)** con permisos de `repo`.
2. Crea tus **Rolla-Balls** de forma visual.
3. Arrastra y sube archivos o imágenes sin límites de tamaño ni errores CORS.
4. Visualiza los distintivos de **versiones acumuladas** en cada objeto.

---

## 🚀 Uso desde el SDK (TypeScript / JavaScript)

```bash
npm install terra-rolla
```

```typescript
import { Rolla } from 'terra-rolla';

const rolla = new Rolla({
  githubToken: process.env.GITHUB_TOKEN // Tu GitHub PAT con permisos de repo
});

// 1. Crear un contenedor (Rolla-Ball)
await rolla.createBall('imagenes-prod');

// 2. Subir un archivo
await rolla.putObject('imagenes-prod', 'fotografia.png', bufferData, {
  contentType: 'image/png'
});

// 3. Listar archivos (devuelve la versión más reciente por defecto)
const objects = await rolla.listObjects('imagenes-prod');
console.log(objects);

// 4. Descargar la última versión del archivo
const buffer = await rolla.getObject('imagenes-prod', 'fotografia.png');

// 5. Historial de Versiones (Object Versioning)
// Al re-subir un objeto con el mismo nombre, Rolla guarda automáticamente las versiones sin sobrescribir las anteriores
await rolla.putObject('imagenes-prod', 'fotografia.png', nuevoBufferData);

// Listar todas las versiones de un objeto
const versiones = await rolla.listObjectVersions('imagenes-prod', 'fotografia.png');
console.log(versiones);

// Descargar una versión específica antigua usando su versionId
const bufferV1 = await rolla.getObject('imagenes-prod', 'fotografia.png', { versionId: versiones[0].versionId });
```

---

## 📜 Licencia

Este proyecto está distribuido bajo la **Licencia MIT**. Siéntete libre de modificarlo, distribuirlo y usarlo en tus aplicaciones privadas o comerciales.

---

<div align="center">
  <sub>Desarrollado con ❤️ para el Ecosistema Terra</sub>
</div>
