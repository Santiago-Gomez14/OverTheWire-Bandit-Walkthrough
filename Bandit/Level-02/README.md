# 🛡️ Bandit Level 02 ➔ Level 03

Documentación técnica sobre el manejo de delimitadores y espacios en blanco en la línea de comandos de Linux. Enfoque en técnicas de escape de caracteres, entrecomillado y procesamiento léxico de argumentos en shells POSIX.

---

## 🎯 Objetivo
Iniciar sesión como `bandit2` y extraer la contraseña de acceso al siguiente nivel almacenada en un archivo cuyo nombre contiene múltiples espacios (`spaces in this filename`) dentro del directorio `$HOME`.

---

## 🧠 Conceptos Técnicos

* **Separación de Palabras (*Word Splitting*):** Por defecto, la shell utiliza los caracteres de la variable interna `$IFS` (espacio, tabulación y salto de línea) como delimitadores para dividir una línea de comando en comando y argumentos independientes.
* **Fallo por Ambigüedad:** Al ejecutar `cat spaces in this filename`, la shell interpreta que se le están pasando 4 archivos distintos como argumentos (`spaces`, `in`, `this`, `filename`), arrojando errores de tipo `No such file or directory`.
* **Mecanismos de Evasión:**
  * **Carácter de escape (`\`):** Anteponer una barra invertida antes de cada espacio anula su significado especial como delimitador y lo preserva como un carácter literal.
  * **Comillas dobles (`"..."`):** Preservan el valor literal de todos los caracteres especiales que delimitan palabras, excepto `$`, `` ` ``, `\` y `!`.
  * **Comillas simples (`'...'`):** Desactivan de forma absoluta cualquier interpretación o expansión especial dentro de la cadena.
  * **Autocompletado (`Tab`):** La shell gestiona automáticamente el escape de caracteres al presionar la tecla Tabulador tras escribir las primeras letras del archivo.

---

## 🛠️ Resolución Paso a Paso

### 1. Conexión remota por SSH
Iniciar sesión con las credenciales obtenidas en el nivel anterior:

```zsh
kitten ssh bandit2@bandit.labs.overthewire.org -p 2220
# O bien: TERM=xterm-256color ssh bandit2@bandit.labs.overthewire.org -p 2220
```
---

### 2. Inspección del archivo objetivo
Listar los contenidos para confirmar la presencia del nombre con espacios:

```Bash
ls -la
```
---

### 3. Lectura del archivo con evasión de espacios

```bash
#Método 1: Escape manual de espacios con barra invertida (\)
cat spaces\ in\ this\ filename

#Método 2: Entrecomillado doble (Recomendado para scripting)
cat "spaces in this filename"

#Método 3: Entrecomillado simple
cat 'spaces in this filename'
```
## 🔑 Credenciales Obtenidas

| Nivel Objetivo | Usuario | Contraseña | Estado |
| :--- | :--- | :---: | :---: |
| **Level 03** | `bandit3` | `[REDACTED]` | 🟢 Obtenida |