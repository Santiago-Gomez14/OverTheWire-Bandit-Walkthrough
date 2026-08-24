# 🛡️ Bandit Level 05 ➔ Level 06

Documentación técnica sobre filtrado y búsqueda avanzada en el árbol del sistema de archivos mediante el comando `find` en Linux.

---

## 🎯 Objetivo
Iniciar sesión como `bandit5` y localizar la contraseña del siguiente nivel dentro del directorio `inhere`, la cual cumple con tres condiciones:
1. Archivo de texto legible por humanos (*human-readable*).
2. Tamaño exacto de **1033 bytes**.
3. No posee permisos de ejecución (*not executable*).

---

## 🧠 Conceptos Técnicos

* **Comando `find`:** Herramienta para buscar archivos y directorios de forma recursiva aplicando filtros por tamaño, tipo, permisos o fechas.
* **Filtros de Búsqueda:**
  * `-type f`: Restringe los resultados únicamente a archivos regulares (excluye carpetas, enlaces y sockets).
  * `-size 1033c`: Busca archivos con un tamaño exacto en bytes (`c` = bytes).
  * `! -executable`: El operador de negación `!` excluye cualquier archivo que tenga permisos de ejecución (`+x`).

---

## 🛠️ Resolución Paso a Paso

### 1. Conexión remota por SSH
Conectarse al servidor con la credencial del nivel anterior:

```zsh
kitten ssh bandit5@bandit.labs.overthewire.org -p 2220
# O bien: TERM=xterm-256color ssh bandit5@bandit.labs.overthewire.org -p 2220
```
---

### 2. Inspección del directorio
Acceder a la carpeta inhere:

```Bash
cd inhere
ls -la
#Nota: La carpeta contiene 20 subdirectorios (maybehere00 a maybehere19), por lo que la búsqueda manual no es viable.
```
---

### 3. Localización del archivo objetivo
Filtrar los archivos del directorio actual según los criterios requeridos:

```Bash
find . -type f -size 1033c ! -executable
Resultado esperado: Retorna la ruta del archivo único (ejemplo: ./maybehere07/.file2).
```
---

### 4. Extracción de la credencial
Leer el contenido del archivo encontrado:

```Bash
cat ./maybehere07/.file2
```
---

## 🔑 Credenciales Obtenidas

| Nivel Objetivo | Usuario | Contraseña | Estado |
| :--- | :--- | :---: | :---: |
| **Level 06** | `bandit6` | `[REDACTED]` | 🟢 Obtenida |