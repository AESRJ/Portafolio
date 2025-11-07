#  Reporte de Laboratorio  
**Práctica:** Instalación del entorno Haskell y desarrollo de aplicación TODO  
**Materia:** Programación Funcional  
**Alumno:** [Jorge Roel Vasquez ]  
**Fecha:** [C]  
**Profesor:** [Carlos Gallegos]

---

##  Objetivo

Instalar correctamente el entorno de desarrollo de **Haskell** mediante el uso de **Stack**, y comprender el funcionamiento de una aplicación tipo **TODO list**, implementada completamente en Haskell.  
Al finalizar, el estudiante deberá ser capaz de ejecutar, modificar y comprender la estructura funcional de la aplicación.

---

##  Materiales y Herramientas

- Sistema operativo: Windows / Linux / macOS  
- Conexión a internet  
- Haskell Platform o Stack  
- Editor de texto (VS Code, Sublime Text, etc.)  
- Terminal o línea de comandos

---

## 🧩 Instalación del Entorno Haskell

### 1. Instalación de Stack

Stack es una herramienta que facilita la instalación y manejo de proyectos Haskell.  
En la terminal, se ejecuta:

```bash

# En Windows (PowerShell)
Set-ExecutionPolicy Bypass -Scope Process -Force;[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; try { & ([ScriptBlock]::Create((Invoke-WebRequest https://www.haskell.org/ghcup/sh/bootstrap-haskell.ps1 -UseBasicParsing))) -Interactive -DisableCurl } catch { Write-Error $_ }


 6. Conclusiones

Haskell es un lenguaje poderoso que promueve la programación funcional pura, lo que lleva a un código más seguro y predecible.

Stack simplifica enormemente la configuración del entorno y la compilación de proyectos Haskell.

Aunque su sintaxis puede parecer compleja al inicio, la estructura de este proyecto TODO demuestra que Haskell puede manejar tareas prácticas de manera elegante y eficiente.

El ejercicio refuerza conceptos como recursión, manejo de listas y acciones de entrada/salida (IO).