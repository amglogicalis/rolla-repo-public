<div align="center">

  <img src="rolla_logo.png" alt="Rolla Storage Engine Logo" width="140" style="filter: drop-shadow(0 0 20px rgba(132, 204, 22, 0.4)); margin-bottom: 1rem;">

  # 📦 ROLLA STORAGE ENGINE
  ### *Motor de Almacenamiento de Objetos Inmutable e Ilimitado a Coste $0*

  [![Ecosistema Terra](https://img.shields.io/badge/Ecosistema-Terra-84cc16?style=for-the-badge&logo=planetScale&logoColor=white)](https://github.com/amglogicalis/Terra)
  [![Consola Web 24/7](https://img.shields.io/badge/Consola%20Web-Desplegada-2ea043?style=for-the-badge&logo=github&logoColor=white)](https://amglogicalis.github.io/rolla-repo-public/)
  [![Licencia MIT](https://img.shields.io/badge/Licencia-MIT-blue.style=for-the-badge)](LICENSE)

</div>

---

## 📌 Visión General

**Rolla** (`@terra/rolla`) es un motor de almacenamiento de objetos inmutable de alto rendimiento (estilo AWS S3) diseñado para el ecosistema **Terra**. Utiliza la infraestructura global de **GitHub Releases & Assets** alojada en la nube de GitHub sobre un repositorio privado (`.rolla-storage`) para ofrecer espacio de almacenamiento ilimitado a **coste $0** sin saturar ramas ni repositorios Git.

---

## 📸 Vista Previa de la Consola Web

<div align="center">
  <img src="rolla_console_preview.png" alt="Rolla Web Console Preview" width="100%" style="border-radius: 12px; border: 1px solid rgba(132, 204, 22, 0.3); box-shadow: 0 10px 30px rgba(0,0,0,0.5);">
</div>

---

## 🌟 Características Destacadas

- ♾️ **Coste $0 e Almacenamiento Ilimitado**: Aprovecha la CDN de Releases de GitHub sin cuotas de subida ni suscripciones.
- 📦 **Rolla-Balls (Buckets)**: Mapeadas internamente como Releases firmadas con tags git `rolla-bkt-<nombre>`.
- ⚡ **Sincronización Instantánea**: Consulta de tags vía Git Refs (`/git/refs/tags`) eliminando latencias de caché.
- 🧩 **Automatic Chunking (>2 GB)**: División y ensamblado transparente para archivos gigantescos.
- 🌐 **Consola Web Estática (GitHub Pages)**: Interfaz cliente 24/7 totalmente responsive para PC y dispositivos móviles.
- 💻 **CLI & Servidor Local**: Herramienta de consola para terminal y servidor local de desarrollo.
- 🔒 **Seguridad y Privacidad**: Tu token PAT se guarda localmente en tu cliente (`localStorage`), jamás en servidores externos.

---

## 💻 Uso desde el CLI (Consola Local)

Puedes lanzar la Consola Web local o interactuar mediante la herramienta de comandos `rolla`:

```bash
# Lanzar la Consola Web Local de Rolla
npx rolla console

# Opción con logs detallados de depuración
npx rolla console --logs
```

---

## 🌐 Uso desde la Consola Web (GitHub Pages)

Accede a la Consola Web desplegada 24/7 desde cualquier navegador de ordenador o teléfono móvil:

👉 **[https://amglogicalis.github.io/rolla-repo-public/](https://amglogicalis.github.io/rolla-repo-public/)**

1. Ingresa tu **GitHub Personal Access Token (PAT)** con permisos de `repo`.
2. Crea tus **Rolla-Balls** de forma visual.
3. Arrastra y sube archivos o imágenes sin límites de tamaño ni errores CORS.

---

## 🚀 Uso desde el SDK (TypeScript / JavaScript)

```bash
npm install @terra/rolla
```

```typescript
import { Rolla } from '@terra/rolla';

const rolla = new Rolla({
  githubToken: process.env.ROLLA_PAT
});

// 1. Crear un contenedor (Rolla-Ball)
await rolla.createBall('imagenes-prod');

// 2. Subir un archivo
await rolla.putObject('imagenes-prod', 'fotografia.png', bufferData, {
  contentType: 'image/png'
});

// 3. Listar archivos
const objects = await rolla.listObjects('imagenes-prod');
console.log(objects);

// 4. Descargar archivo
const buffer = await rolla.getObject('imagenes-prod', 'fotografia.png');
```

---

## 📜 Licencia

Este proyecto está distribuido bajo la **Licencia MIT**. Siéntete libre de modificarlo, distribuirlo y usarlo en tus aplicaciones privadas o comerciales. Consulta el archivo `LICENSE` para más detalles.

---

<div align="center">
  <sub>Desarrollado con ❤️ para el Ecosistema Terra</sub>
</div>
