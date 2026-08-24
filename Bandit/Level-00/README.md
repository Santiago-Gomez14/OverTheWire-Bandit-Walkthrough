# 🛡️ Bandit Level 00 ➔ Level 01

Documentación técnica del nivel inicial del laboratorio. Enfoque en conexiones remotas cifradas mediante el protocolo SSH en puertos no estándar, resolución de compatibilidad de emuladores de terminal modernos y lectura básica de archivos en Linux.

---

## 🎯 Objetivo
Establecer una sesión interactiva segura por SSH con el servidor de *OverTheWire* utilizando las credenciales base (`bandit0` / `bandit0`) y extraer la credencial de acceso al siguiente nivel alojada en el archivo `readme` dentro del directorio `$HOME`.

---

## 🧠 Conceptos Técnicos

* **Protocolo SSH (Secure Shell):** Protocolo de administración remota cifrado que opera por defecto en la capa de aplicación sobre el puerto `22/TCP`.
* **Especificación de Puerto Alternativo (`-p 2220`):** En este entorno se utiliza el puerto no estándar `2220`. La bandera `-p` fuerza al cliente SSH a enlazar con dicho puerto.
* **Compatibilidad de Terminfo (`xterm-kitty`):** Al conectarse desde emuladores modernos como *Kitty* con *Zsh*, el servidor remoto puede carecer de las definiciones de terminal locales (`terminfo`). Para evitar fallos de renderizado o errores al limpiar pantalla, se transfiere la definición con `kitten ssh` o se normaliza la variable de entorno a `TERM=xterm-256color`.

---

## 🛠️ Resolución Paso a Paso

### 1. Conexión remota autenticada (Entorno Kitty / Zsh)
Iniciar la sesión SSH forzando la compatibilidad de terminal y el puerto de escucha:

```zsh
# Opción recomendada en Kitty (gestiona terminfo automáticamente):
kitten ssh bandit0@bandit.labs.overthewire.org -p 2220

# Opción estándar forzando emulación xterm:
TERM=xterm-256color ssh bandit0@bandit.labs.overthewire.org -p 2220

```

### 2. Inspección del directorio $HOME
Verificar los permisos, propietario y tamaño del contenido del directorio de trabajo:

# Listar todos los archivos con metadatos
```bash
ls -la
```
### 3. Extracción de la credencial
Leer el flujo de texto del archivo objetivo:

# Imprimir contenido en stdout
```bash
cat readme
```
## 🔑 Credenciales Obtenidas

| Nivel Objetivo | Usuario | Contraseña | Estado |
| :--- | :--- | :---: | :---: |
| **Level 01** | `bandit1` | `[REDACTED]` | 🟢 Obtenida |