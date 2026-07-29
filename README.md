# 📦 ROLLA STORAGE Engine — Terra Ecosystem
> **Immutable, Infinite Object Storage System at $0 Cost**

[![Terra Ecosystem](https://img.shields.io/badge/Ecosystem-Terra-84cc16?style=for-the-badge&logo=planetScale&logoColor=white)](https://github.com/amglogicalis/Terra)
[![GitHub Pages](https://img.shields.io/badge/Web%20Console-Live-2ea043?style=for-the-badge&logo=github&logoColor=white)](https://amglogicalis.github.io/rolla-repo-public/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.style=for-the-badge)](LICENSE)

<p center="text-align">
  <img src="rolla_logo.png" alt="Rolla Storage Logo" width="120" style="filter: drop-shadow(0 0 15px rgba(132, 204, 22, 0.4));">
</p>

**Rolla** (`@terra/rolla`) es un motor de almacenamiento de objetos inmutable de alto rendimiento (equivalente a AWS S3) construido para el ecosistema **Terra**. Utiliza la infraestructura de **GitHub Releases & Assets** sobre un repositorio privado (`.rolla-storage`) para ofrecer espacio de almacenamiento ilimitado a coste $0 con soporte para archivos masivos (>2 GB) mediante *chunking* automático.

---

## 🌟 Características Principales

- ♾️ **Coste $0 e ilimitado**: Sin gastos mensuales de almacenamiento ni transferencia.
- 📦 **Rolla-Balls (Buckets)**: Contenedores aislados mapeados internamente como Releases de GitHub.
- ⚡ **Lectura Instantánea sin Caché**: Sincronización en tiempo real vía Git Refs (`/git/refs/tags`).
- 🧩 **Automatic Chunking (>2 GB)**: División y ensamblado automático de archivos de gran tamaño.
- 🌐 **Consola Web 24/7 (GitHub Pages)**: Interfaz cliente pura desatendida para ordenador y dispositivos móviles.
- 💻 **Consola Local & SDK**: SDK oficial TypeScript/Node.js para integración en aplicaciones y CLI local.

---

## 📸 Consola Web & Interfaz

La Consola Web Estática está alojada y disponible en GitHub Pages:  
👉 **[https://amglogicalis.github.io/rolla-repo-public/](https://amglogicalis.github.io/rolla-repo-public/)**

---

## 🚀 Inicio Rápido (SDK Node.js)

```bash
npm install @terra/rolla
```

```typescript
import { Rolla } from '@terra/rolla';

const rolla = new Rolla({
  githubToken: process.env.ROLLA_PAT
});

// Crear una Rolla-Ball
await rolla.createBall('imagenes-prod');

// Subir un Objeto
await rolla.putObject('imagenes-prod', 'foto.png', bufferData, {
  contentType: 'image/png'
});

// Listar Objetos
const objects = await rolla.listObjects('imagenes-prod');
console.log(objects);
```

---

## 🔒 Privacidad y Seguridad

Tu Personal Access Token (PAT) de GitHub **se almacena localmente en tu navegador / entorno local**. Jamás pasa por servidores ni bases de datos de terceros.

---

<p center="text-align">
  <i>Desarrollado con ❤️ para el Ecosistema Terra</i>
</p>
