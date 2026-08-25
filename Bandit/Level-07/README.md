# 🛡️ Bandit Level 07 ➔ Level 08

Documentación técnica sobre procesamiento de flujos de texto, filtrado por patrones y expresiones regulares básicas utilizando la utilidad `grep` en Linux.

---

## 🎯 Objetivo
Iniciar sesión como `bandit7` y extraer la contraseña del siguiente nivel alojada en el archivo `data.txt`, ubicada inmediatamente al lado de la palabra clave **`millionth`**.

---

## 🧠 Conceptos Técnicos

* **Comando `grep` (*Global Regular Expression Print*):** Herramienta estándar para escanear archivos o flujos de entrada en busca de líneas que coincidan con un patrón o texto específico.
* **Procesamiento de Archivos Voluminosos:** El archivo `data.txt` contiene miles de registros aleatorios, lo que imposibilita la lectura manual con `cat` o `less`.
* **Procesamiento por Columnas (`awk` / `cut`):** Utilidades complementarias para segmentar cadenas delimitadas por espacios/tabulaciones y aislar campos concretos.

---

## 🛠️ Resolución Paso a Paso

### 1. Conexión remota por SSH
Autenticarse con la credencial del nivel previo:

```zsh
kitten ssh bandit7@bandit.labs.overthewire.org -p 2220
# O bien: TERM=xterm-256color ssh bandit7@bandit.labs.overthewire.org -p 2220
```
---

### 2. Inspección del archivo de datos
Comprobar las dimensiones del archivo en el $HOME:

```Bash
ls -lh data.txt
wc -l data.txt
# Nota: El fichero contiene alrededor de 85.000 líneas.
```
---

### #3. Filtrado y extracción de la credencial
```Bash
#Método 1: Búsqueda directa con grep (Recomendado)
grep "millionth" data.txt

#Método 2: Filtrado por tubería (pipeline)
cat data.txt | grep "millionth"

#Método 3: Extracción directa de la columna con awk
awk '/millionth/ {print $2}' data.txt
```
---

## 🔑 Credenciales Obtenidas

| Nivel Objetivo | Usuario | Contraseña | Estado |
| :--- | :--- | :---: | :---: |
| **Level 08** | `bandit8` | `[REDACTED]` | 🟢 Obtenida |