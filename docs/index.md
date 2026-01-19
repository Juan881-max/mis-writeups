# 🛡️ Auditoría de Seguridad: Máquina Backend

¡Bienvenido a mi repositorio de Writeups! En este espacio documento mis resoluciones de máquinas de CTF y laboratorios de hacking ético.

---

## 🏗️ Ficha Técnica - Backend
* [cite_start]**Plataforma:** DockerLabs [cite: 2]
* [cite_start]**Dificultad:** Fácil [cite: 2]
* **Fecha:** Enero 2026
* **Técnicas Clave:** SQL Injection, BurpSuite, SUID Exploitation.

---

## 🔍 Resumen de la Intrusión

### 1. Reconocimiento e Identificación
[cite_start]Tras realizar un escaneo con `nmap`, identifiqué los puertos **22 (SSH)** y **80 (HTTP)** abiertos. [cite: 4, 7, 17] [cite_start]El servidor web Apache 2.4.61 presentaba un panel de login vulnerable a inyecciones SQL basadas en errores. [cite: 18, 23, 41]

### 2. Explotación (Web Entry)
[cite_start]Utilicé **BurpSuite** para capturar la petición de autenticación y **sqlmap** para automatizar la extracción de datos. [cite: 43, 62, 63]
* [cite_start]**Base de Datos identificada:** `users` [cite: 69]
* [cite_start]**Credenciales extraídas:** Acceso exitoso mediante el usuario `pepe`. [cite: 96, 103]

### 3. Escalada de Privilegios
[cite_start]Una vez dentro del sistema vía SSH, identifiqué binarios con el bit **SUID** activado. [cite: 103, 106, 108]
* [cite_start]**Vectores hallados:** `/usr/bin/ls` y `/usr/bin/grep`. [cite: 111, 116]
* [cite_start]**Explotación:** Aproveché los privilegios de `grep` para leer el archivo `/root/pass.hash`. [cite: 125, 127]
* [cite_start]**Cracking:** El hash MD5 `e43833c4c9d5ac444e16bb94715a75e4` resultó ser la contraseña `spongebob34`. [cite: 125, 131, 149]

---

## 📂 Archivos del Proyecto
* [cite_start][Descargar Informe Completo (PDF)](./DockerLabs/Facil/Backend/backend.pdf) [cite: 1, 2]

---
*Escrito por Juan881-max - Apasionado por la Ciberseguridad y el Pentesting.*
