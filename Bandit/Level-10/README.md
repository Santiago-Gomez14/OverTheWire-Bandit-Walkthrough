# 🛡️ Bandit Level 10 ➔ Level 11

Documentación técnica sobre esquemas de codificación de datos, análisis del algoritmo Base64 y decodificación de flujos mediante la utilidad `base64` en Linux.

---

## 🎯 Objetivo
Iniciar sesión como `bandit10` y obtener la credencial para el siguiente nivel decodificando el contenido del archivo `data.txt`, el cual almacena los datos codificados en formato **Base64**.

---

## 🧠 Conceptos Técnicos

* **Codificación Base64 (RFC 4648):** Esquema de representación binaria a texto que transforma secuencias de bytes en un conjunto seguro de 64 caracteres ASCII imprimibles (`A-Z`, `a-z`, `0-9`, `+`, `/` y `=` como relleno/*padding*).
* **Codificación vs. Cifrado:** Base64 **no es cifrado**; no proporciona confidencialidad ni requiere claves secretas, solo es un formato de serialización para transportar datos de forma íntegra a través de canales que solo admiten texto.
* **Comando `base64`:** Utilidad estándar del paquete GNU Coreutils para codificar y decodificar datos desde un archivo o desde la entrada estándar (`stdin`).
  * `-d` o `--decode`: Bandera que conmuta el comportamiento por defecto (codificar) para revertir los datos a su forma original legible.

---

## 🛠️ Resolución Paso a Paso

### 1. Conexión remota por SSH
Iniciar sesión con la credencial obtenida en el nivel anterior:

```zsh
kitten ssh bandit10@bandit.labs.overthewire.org -p 2220
# O bien: TERM=xterm-256color ssh bandit10@bandit.labs.overthewire.org -p 2220
```
---

### 2. Inspección del archivo codificado
Verificar el formato del texto contenido en $HOME:

```Bash
cat data.txt
# Salida: Cadena de caracteres ASCII finalizada en =.
```
---

### 3. Decodificación y extracción de la credencial

```bash
# Método 1: Decodificación directa del archivo (Recomendado)
base64 -d data.txt

# Método 2: Procesamiento mediante pipeline
cat data.txt | base64 --decode

# Método 3: Extracción automatizada del valor limpio con awk
base64 -d data.txt | awk '{print $NF}'
```
---

## 🔑 Credenciales Obtenidas

| Nivel Objetivo | Usuario | Contraseña | Estado |
| :--- | :--- | :---: | :---: |
| **Level 11** | `bandit11` | `[REDACTED]` | 🟢 Obtenida |
