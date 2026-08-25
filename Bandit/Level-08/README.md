# 🛡️ Bandit Level 08 ➔ Level 09

Documentación técnica sobre análisis de frecuencia de datos, ordenamiento de flujos de texto y filtrado de registros únicos mediante la combinación de `sort` y `uniq` en Linux.

---

## 🎯 Objetivo
Iniciar sesión como `bandit8` y extraer la contraseña del siguiente nivel ubicada en el archivo `data.txt`, la cual corresponde a la **única línea de texto que no se repite** (ocurre exactamente una sola vez entre miles de líneas duplicadas).

---

## 🧠 Conceptos Técnicos

* **Limitación de `uniq`:** La utilidad `uniq` solo detecta y descarta líneas duplicadas que sean **adyacentes** (consecutivas). Si dos líneas iguales están separadas por otras, `uniq` no las identificará como duplicados.
* **Comando `sort`:** Reordena alfabética o numéricamente las líneas de un flujo de texto, agrupando automáticamente todas las líneas idénticas de forma contigua.
* **Flag `uniq -u` (*Unique*):** A diferencia del comportamiento por defecto (que imprime una copia de cada línea), el parámetro `-u` imprime **únicamente** aquellas líneas que no presentan duplicados en todo el archivo.
* **Tuberías (*Pipes* `|`):** Redirige el `stdout` de `sort` directamente al `stdin` de `uniq` para procesar el flujo en memoria sin generar archivos temporales en disco.

---

## 🛠️ Resolución Paso a Paso

### 1. Conexión remota por SSH
Iniciar sesión con la credencial del nivel anterior:

```zsh
kitten ssh bandit8@bandit.labs.overthewire.org -p 2220
# O bien: TERM=xterm-256color ssh bandit8@bandit.labs.overthewire.org -p 2220
```
---

### 2. Inspección del archivo
Verificar la estructura y tamaño del archivo en el $HOME:

```Bash
ls -lh data.txt
```
---

### 3. Ordenamiento y extracción de la línea única

```bash
# Método 1: Pipeline estándar (Recomendado)
sort data.txt | uniq -u

# Método 2: Conteo de ocurrencias (Frequency analysis)
# Ordena, cuenta repeticiones (-c) y filtra las que tengan conteo igual a 1
sort data.txt | uniq -c | grep " 1 "
```
---

## 🔑 Credenciales Obtenidas

| Nivel Objetivo | Usuario | Contraseña | Estado |
| :--- | :--- | :---: | :---: |
| **Level 09** | `bandit9` | `[REDACTED]` | 🟢 Obtenida |