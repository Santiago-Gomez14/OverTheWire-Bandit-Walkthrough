# 🛡️ Bandit Level 03 ➔ Level 04

Documentación técnica sobre la gestión e inspección de archivos ocultos (*dotfiles*) y navegación de directorios en entornos Unix/Linux.

---

## 🎯 Objetivo
Autenticarse como `bandit3` y recuperar la contraseña para el siguiente nivel, la cual se encuentra almacenada dentro de un archivo oculto ubicado en el subdirectorio `inhere`.

---

## 🧠 Conceptos Técnicos

* **Archivos Ocultos (*Dotfiles*):** En la convención de sistemas tipo Unix, cualquier archivo o directorio cuyo nombre comience con un punto (`.`) es tratado como oculto por defecto por las utilidades del sistema.
* **Comportamiento del comando `ls`:** Por defecto, `ls` omite listar entradas que comienzan con `.`. 
* **Flags de visualización completa:**
  * `-a` (*all*): Fuerza a `ls` a listar todas las entradas, incluyendo los archivos ocultos y los pseudodirectorios `.` (directorio actual) y `..` (directorio padre).
  * `-la`: Combina el listado largo (permisos, propietario, tamaño, fecha) con la visualización de archivos ocultos.

---

## 🛠️ Resolución Paso a Paso

### 1. Conexión remota por SSH
Iniciar sesión con la credencial obtenida en el nivel anterior:

```zsh
kitten ssh bandit3@bandit.labs.overthewire.org -p 2220
# O bien: TERM=xterm-256color ssh bandit3@bandit.labs.overthewire.org -p 2220
```
---

### 2. Navegación al directorio objetivo
Ingresar a la carpeta inhere presente en el $HOME:

```bash
cd inhere
```
---

### 3. Revelado del archivo oculto
Inspeccionar el directorio incluyendo archivos protegidos/ocultos:

```bash
# Listado detallado mostrando dotfiles
ls -la
# Resultado esperado: Identificación del archivo .hidden.
```
---

### 4. Extracción de la credencial
Leer el archivo oculto en consola:

```Bash
cat .hidden
```
---

## 🔑 Credenciales Obtenidas

| Nivel Objetivo | Usuario | Contraseña | Estado |
| :--- | :--- | :---: | :---: |
| **Level 04** | `bandit4` | `[REDACTED]` | 🟢 Obtenida |