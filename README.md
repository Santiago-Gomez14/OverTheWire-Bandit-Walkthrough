# 🛡️ OverTheWire: Bandit Walkthrough & Linux Security Labs

Repositorio con la resolución técnica, razonada y documentada de los wargames de **OverTheWire (Bandit)**. Orientado al dominio práctico de la CLI de Linux, procesamiento de flujos de texto, análisis de permisos del sistema y seguridad informática básica.

---

## 📊 Matriz de Progreso y Comandos Dominados

| Rango de Niveles | Temas Principales | Herramientas y Comandos Clave | Documentación |
| :--- | :--- | :--- | :---: |
| **Bandit 00 ➔ 05** | Conexiones SSH, archivos especiales (`-`), espacios, ficheros ocultos y tipos de datos (*magic numbers*). | `ssh`, `cat`, `ls -la`, `file`, `find`, `xargs` | [Ver Walkthrough](Bandit/Level-00-to-05.md) |
| **Bandit 06 ➔ 10** | Búsquedas avanzadas por atributos (`size`, `user`, `group`), filtrado con `grep`, ordenamiento y análisis con `awk` / `strings`. | `find`, `grep`, `sort`, `uniq -u`, `strings`, `awk`, `tail` | [Ver Walkthrough](Bandit/Level-06-to-10.md) |

---

## 🛠️ Tecnologías y Entorno de Pruebas
* **OS:** Linux (Parrot Security / Debian based)
* **Shell:** Bash / Zsh
* **Terminal Emulator:** Kitty / Tmux
* **Enfoque:** 100% interactivo mediante línea de comandos (CLI) y pipelines (`|`).

---

## 🔒 Política Ética
De acuerdo con las normativas de los wargames y la ética profesional en ciberseguridad, las contraseñas y credenciales finales se encuentran ofuscadas (`[REDACTED]`). La documentación prioriza el análisis, los conceptos teóricos y la lógica de resolución de cada desafío.
