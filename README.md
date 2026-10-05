<div align="center">

<img src="assets/banner.png" width="100%" alt="Banner de mibudget, control quincenal de presupuesto">

# mibudget

![Privado](https://img.shields.io/badge/C%C3%B3digo-Privado%20%C2%B7%20Proyecto%20Propio-red?style=flat)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express%204-000000?style=flat&logo=express&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat&logo=sqlite&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![PM2](https://img.shields.io/badge/PM2-2B037A?style=flat&logo=pm2&logoColor=white)

**Aplicación web de presupuesto quincenal: reparte cada quincena en sobres, controla cuentas fijas, deudas y ahorro, proyecta el flujo de caja y protege todo con inicio de sesión y respaldos automáticos.**

</div>

> Este es un **portafolio showcase**: el código fuente es propietario y no está incluido. Las capturas usan datos de ejemplo.

---

## Contenido

- [El Problema](#el-problema)
- [La Solución](#la-solución)
- [Funcionalidades](#funcionalidades)
- [Vista Previa](#vista-previa)
- [Arquitectura](#arquitectura)
- [Stack Tecnológico](#stack-tecnológico)
- [Instalación local](#instalación-local)
- [Roadmap](#roadmap)
- [Contacto](#contacto)

---

## El Problema

Llevar el presupuesto personal en una hoja de cálculo se vuelve difícil cuando se cobra por quincena:

- No es claro cuánto queda libre después de apartar lo que ya está comprometido.
- Los pagos fijos, las suscripciones y las deudas se pierden entre filas.
- Proyectar el ahorro y el pago de un préstamo exige fórmulas fáciles de romper.
- Los datos financieros deben estar protegidos y respaldados.

---

## La Solución

Una aplicación ligera con un servidor Express y una interfaz en JavaScript sin frameworks pesados. Cada quincena se reparte en sobres y cuentas fijas, el simulador proyecta el flujo de caja y la amortización, y todo el estado se guarda en SQLite con copias de respaldo con fecha. El acceso se protege con contraseña y una política de seguridad de contenido (CSP) estricta.

---

## Funcionalidades

| Funcionalidad | Descripción |
|---------------|-------------|
| Panel de inicio | Saldo libre disponible, fondos asignados por cuenta y presupuesto de la quincena |
| Sobres y cuentas fijas | Apartados quincenales y suscripciones con su estado de pago |
| Simulador y proyección | Hoja de ruta por fases y flujo de caja proyectado quincena a quincena |
| Ahorro y deudas | Ahorro grupal con rendimiento, amortización de deudas y préstamo quincenal |
| Respaldos | Copia con fecha en cada guardado (se conservan las últimas 30), descarga de respaldo y exportación a SQLite |
| Persistencia segura | SQLite en modo WAL con transacciones y escritura atómica |
| Acceso protegido | Inicio de sesión con contraseña y CSP estricta en el navegador |
| Pruebas automáticas | Pruebas con el ejecutor nativo de Node.js sobre los cálculos, la API y la base de datos |

---

## Vista Previa

<img src="assets/screenshots/01-inicio.png" width="100%" alt="Panel de inicio con saldo libre, fondos asignados y presupuesto de la quincena">

<table>
  <tr>
    <td width="50%">
      <img src="assets/screenshots/02-simulador.png" width="100%" alt="Hoja de ruta estratégica y flujo de caja proyectado">
      <br><b>Hoja de ruta</b>: fases del plan financiero y flujo de caja quincena a quincena.
    </td>
    <td width="50%">
      <img src="assets/screenshots/03-sobres.png" width="100%" alt="Sobres y cuentas fijas de la quincena">
      <br><b>Sobres y cuentas fijas</b>: apartados quincenales y suscripciones con su estado.
    </td>
  </tr>
  <tr>
    <td width="50%">
      <img src="assets/screenshots/05-sociedad.png" width="100%" alt="Ahorro grupal, deuda y préstamo">
      <br><b>Ahorro y deudas</b>: ahorro grupal, amortización de una deuda y préstamo quincenal.
    </td>
    <td width="50%"></td>
  </tr>
</table>

---

## Arquitectura

```mermaid
graph LR
    CLIENT["Navegador<br/>JavaScript · HTML · CSS<br/>cálculos en el cliente"]
    SERVER["Servidor<br/>Node.js · Express 4<br/>sesión + CSP estricta"]
    DB[("SQLite<br/>modo WAL")]
    BK[("Respaldos con fecha<br/>últimas 30 copias")]

    CLIENT -->|"API REST con sesión"| SERVER
    SERVER -->|"Transacciones"| DB
    SERVER -->|"Copia en cada guardado"| BK
```

**Rutas del servidor:** autenticación, presupuesto y respaldos. La política CSP prohíbe scripts y estilos en línea, así que los valores dinámicos se aplican desde JavaScript.

---

## Stack Tecnológico

| Capa | Tecnología |
|------|-----------|
| Frontend | JavaScript sin frameworks · HTML · CSS |
| Backend | Node.js · Express 4 |
| Datos | SQLite nativo de Node.js (modo WAL) |
| Seguridad | Sesiones con contraseña · CSP estricta |
| Pruebas | Ejecutor de pruebas nativo de Node.js |
| Despliegue | PM2 · Nginx |

---

## Instalación local

> **Aviso:** el código es privado y propietario. Estos pasos son solo para colaboradores autorizados con acceso al repositorio.

1. Instala una versión reciente de Node.js.
2. Instala las dependencias:
   ```bash
   npm install
   ```
3. Crea un archivo `.env` con tus propios valores de acceso y de sesión.
4. Inicia el servidor:
   ```bash
   npm start
   ```
5. Ejecuta las pruebas:
   ```bash
   npm test
   ```

---

## Roadmap

- [ ] Ampliar las pruebas automáticas a las pantallas del frontend.
- [ ] Gráficos adicionales de gasto por categoría.

---

## Contacto

El código fuente es propietario. Para consultas o propuestas, escríbeme:

[![Email](https://img.shields.io/badge/Email-pablozam1931%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:pablozam1931@gmail.com)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-(507)%206517--1870-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/50765171870)
[![GitHub](https://img.shields.io/badge/GitHub-deadlyrat-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/deadlyrat)

- Correo: [pablozam1931@gmail.com](mailto:pablozam1931@gmail.com)
- WhatsApp: [(507) 6517-1870](https://wa.me/50765171870)
- GitHub: [github.com/deadlyrat](https://github.com/deadlyrat)

---

*Parte del portafolio de [deadlyrat](https://github.com/deadlyrat)*
