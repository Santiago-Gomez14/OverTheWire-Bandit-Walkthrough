# 🛡️ Bandit Level 04 ➔ Level 05

Documentación técnica sobre inspección de tipos de archivos (*file signatures* y *magic numbers*), discriminación entre datos binarios y texto legible por humanos (*ASCII text*), y procesamiento seguro de comodines en Linux.

---

## 🎯 Objetivo
Iniciar sesión como `bandit4` y extraer la contraseña del siguiente nivel alojada en el único archivo con texto legible por humanos (*human-readable*) dentro del directorio `inhere`, entre múltiples archivos binarios con nombres que inician con guion (`-file00` a `-file09`).

---

## 🧠 Conceptos Técnicos

* **Comando `file`:** Herramienta que determina el tipo de datos de un archivo analizando su cabecera y números mágicos (*magic numbers*), sin depender de la extensión del fichero.
* **Texto legible (*ASCII / UTF-8 text*):** A diferencia de los ficheros binarios o de datos crudos (`data`), los archivos de texto contienen únicamente secuencias de caracteres imprimibles estándar.
* **Expansión de Comodines Segura (*Globbing* con `./*`):** Si se ejecuta `file *`, los archivos con prefijo `-` serán interpretados por el comando como opciones no válidas. Al usar `./*`, la shell antepone la ruta relativa y neutraliza la interpretación de flags.

---

## 🛠️ Resolución Paso a Paso

### 1. Conexión remota por SSH
Iniciar sesión con la credencial del nivel anterior:

```zsh
kitten ssh bandit4@bandit.labs.overthewire.org -p 2220
# O bien: TERM=xterm-256color ssh bandit4@bandit.labs.overthewire.org -p 2220
```
---

### 2. Navegación al directorio objetivo
Ingresar a la carpeta de trabajo:

```Bash
cd inhere
```
---

### 3. Identificación del archivo de texto con file
Escanear masivamente todos los nodos del directorio:

```Bash
file ./*
#Salida esperada: Casi todos los archivos retornarán data, excepto uno que devolverá ASCII text (habitualmente ./-file07).
```
---

### 4. Extracción de la credencial
Leer el archivo identificado utilizando la referencia de ruta relativa:

```Bash
cat ./-file07
```
---

## 🔑 Credenciales Obtenidas

| Nivel Objetivo | Usuario | Contraseña | Estado |
| :--- | :--- | :---: | :---: |
| **Level 05** | `bandit5` | `[REDACTED]` | 🟢 Obtenida |
