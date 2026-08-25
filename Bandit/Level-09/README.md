# 🛡️ Bandit Level 09 ➔ Level 10

Documentación técnica sobre extracción de cadenas de caracteres imprimibles (*strings*) en archivos con contenido binario y filtrado por patrones repetitivos en Linux.

---

## 🎯 Objetivo
Iniciar sesión como `bandit9` y recuperar la contraseña del siguiente nivel alojada en el archivo `data.txt`, la cual está contenida en una de las pocas cadenas de texto legible por humanos y precedida por múltiples caracteres de igual (`=`).

---

## 🧠 Conceptos Técnicos

* **Comando `strings`:** Herramienta que escanea archivos binarios o no estructurados e imprime secuencias continuas de caracteres imprimibles (por defecto, de al menos 4 caracteres de longitud) seguidas de un carácter no imprimible o salto de línea.
* **Corrupción de Terminal por Datos Binarios:** Ejecutar `cat` sobre un archivo de datos binarios (`data`) puede enviar códigos de escape que desconfiguren la visualización de la terminal. `strings` sanitiza el flujo extrayendo únicamente texto legible.
* **Filtrado Combinado (`strings` + `grep`):** Permite canalizar la salida limpia de texto hacia `grep` para aislar la línea exacta que contiene el patrón delimitador (`===`).

---

## 🛠️ Resolución Paso a Paso

### 1. Conexión remota por SSH
Autenticarse con la credencial del nivel anterior:

```zsh
kitten ssh bandit9@bandit.labs.overthewire.org -p 2220
# O bien: TERM=xterm-256color ssh bandit9@bandit.labs.overthewire.org -p 2220
```
---

### 2. Inspección del tipo de archivo
Comprobar la naturaleza del archivo con file:

```Bash
file data.txt
#Salida esperada: data.txt: data (indica contenido binario/datos crudos).
```
---

### 3. Extracción automatizada de la credencial
Canalizar la salida de texto legible, filtrar el delimitador, aislar la última coincidencia y extraer el valor de la clave limpia:

```bash
strings data.txt | grep "===" | tail -n 1 | awk '{print $NF}'

# Notas: Desglose del pipeline:
strings data.txt # Sanitiza el archivo binario extrayendo solo texto imprimible.
grep "===" # Filtra las líneas que contienen el delimitador del laboratorio.
tail -n 1 # Aísla la última ocurrencia (donde se ubica la clave real).
awk '{print $NF}' # Imprime directamente la última columna con el string de la contraseña.
```

## 🔑 Credenciales Obtenidas

| Nivel Objetivo | Usuario | Contraseña | Estado |
| :--- | :--- | :---: | :---: |
| **Level 10** | `bandit10` | `[REDACTED]` | 🟢 Obtenida |


