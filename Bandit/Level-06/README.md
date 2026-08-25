# 🛡️ Bandit Level 06 ➔ Level 07

Documentación técnica sobre búsqueda recursiva en la raíz del sistema (`/`), filtrado por propietario/grupo y gestión de descriptores de error estándar (`stderr`) en Linux.

---

## 🎯 Objetivo
Autenticarse como `bandit6` y localizar la contraseña del siguiente nivel en cualquier parte del sistema de archivos, la cual cumple con tres propiedades:
1. Pertenecer al usuario `bandit7`.
2. Pertenecer al grupo `bandit6`.
3. Tener un tamaño exacto de **33 bytes**.

---

## 🧠 Conceptos Técnicos

* **Búsqueda global (`/`):** Al buscar desde el directorio raíz, el comando intentará acceder a directorios del sistema y de otros usuarios a los que no tiene permisos de lectura.
* **Descriptores de Archivo en Linux:**
  * `0` = Entrada estándar (`stdin`).
  * `1` = Salida estándar (`stdout`).
  * `2` = Error estándar (`stderr`).
* **Supresión de Errores (`2>/dev/null`):** Redirige el flujo de errores (`Permission denied`) al dispositivo nulo `/dev/null` para descartarlos y mantener la salida de la terminal limpia.
* **Filtros de `find`:**
  * `-user <nombre>`: Filtra por usuario propietario.
  * `-group <nombre>`: Filtra por grupo propietario.
  * `-size 33c`: Filtra por tamaño exacto en bytes (`c`).

---

## 🛠️ Resolución Paso a Paso

### 1. Conexión remota por SSH
Iniciar sesión con las credenciales del nivel anterior:

```zsh
kitten ssh bandit6@bandit.labs.overthewire.org -p 2220
# O bien: TERM=xterm-256color ssh bandit6@bandit.labs.overthewire.org -p 2220
```
---

### 2. Búsqueda y descarte de ruido
Ejecutar el escaneo desde la raíz redirigiendo los errores:

```Bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
# Resultado esperado: Retorna la ruta absoluta del archivo objetivo (/var/lib/dpkg/info/bandit7.password).
```
---

### 3. Extracción de la credencial
Leer el archivo localizado:

```Bash
cat /var/lib/dpkg/info/bandit7.password
```
---

## 🔑 Credenciales Obtenidas

| Nivel Objetivo | Usuario | Contraseña | Estado |
| :--- | :--- | :---: | :---: |
| **Level 07** | `bandit7` | `[REDACTED]` | 🟢 Obtenida |

