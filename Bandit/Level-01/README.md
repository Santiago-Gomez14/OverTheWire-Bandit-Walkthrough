# 🛡️ Bandit Level 01 ➔ Level 02

Documentación técnica sobre el manejo de archivos especiales en sistemas POSIX. Enfoque en la resolución de colisiones entre nombres de archivos y opciones de línea de comandos en la shell de Unix.

---

## 🎯 Objetivo
Autenticarse como `bandit1` y extraer la contraseña del siguiente nivel alojada en un archivo llamado literalmente `-` (guion medio) en el directorio `$HOME`.

---

## 🧠 Conceptos Técnicos

* **Convención POSIX del Guion (`-`):** En la mayoría de las herramientas estándar de Linux (`cat`, `grep`, `tar`, `awk`), un guion solitario como argumento representa la **entrada estándar (`stdin`)** en lugar de una ruta de archivo.
* **Ambigüedad de Flags:** Cuando una utilidad lee un argumento que comienza con `-`, el analizador léxico (*parser*) de la shell lo interpreta como una opción/bandera de configuración y no como un archivo físico.
* **Ruptura de Ambigüedad:**
  * **Ruta relativa explícita (`./-`):** Al anteponer `./`, el nombre del archivo ya no comienza con `-`, forzando al sistema de archivos a resolver la ruta relativa.
  * **Delimitador de fin de opciones (`--`):** Le indica al comando que todos los argumentos subsiguientes deben tratarse como operandos/archivos, deshabilitando el procesamiento de flags.

---

## 🛠️ Resolución Paso a Paso

### 1. Conexión remota por SSH
Iniciar sesión con las credenciales obtenidas en el nivel previo:

```zsh
kitten ssh bandit1@bandit.labs.overthewire.org -p 2220
# O bien: TERM=xterm-256color ssh bandit1@bandit.labs.overthewire.org -p 2220
```
### 2. Identificación del archivo especial
Inspeccionar el directorio de trabajo para confirmar la existencia del nodo:
```bash
#Método 1: Ruta relativa explícita (Recomendado)
cat ./-

#Método 2: Delimitador estándar POSIX (--)
cat -- -

#Método 3: Redirección de entrada estándar (<)
cat < -
```
## 🔑 Credenciales Obtenidas

| Nivel Objetivo | Usuario | Contraseña | Estado |
| :--- | :--- | :---: | :---: |
| **Level 02** | `bandit2` | `[REDACTED]` | 🟢 Obtenida |