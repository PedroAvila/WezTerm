# Guía Completa: Neovim + LazyVim + WezTerm en Windows 11 (con soporte para Angular y TypeScript)

Esta guía reúne todos los pasos, comandos, verificaciones y atajos necesarios para instalar, configurar y solucionar la compilación de parsers de Tree-sitter (`nvim-treesitter`) en Windows 11 utilizando **WezTerm**, **Neovim**, **LazyVim** y **GCC (WinLibs)**.

---

## 1. Instalación de herramientas base con `winget`

Abre una ventana de PowerShell o **WezTerm** y ejecuta los siguientes comandos para instalar Neovim, WezTerm, Git y el compilador GCC (necesario para compilar los parsers de `nvim-treesitter` sin errores de `cl.exe`):

```powershell
winget install Neovim.Neovim
winget install wez.wezterm
winget install Git.Git
winget install BrechtSanders.WinLibs.POSIX.UCRT
```

> **Nota importante:** Si previamente creaste la variable de entorno de usuario `CC` apuntando a `zig cc` (lo cual genera el error `unable to parse target query 'x86_64-pc-windows-msvc': UnknownOperatingSystem` con `tree-sitter-cli`), elimínala con:
>
> ```powershell
> [Environment]::SetEnvironmentVariable("CC", $null, "User")
> ```

### Verificación

Cierra por completo todas las ventanas de la terminal y vuelve a abrir **WezTerm** para que Windows actualice el `PATH`. Luego verifica que las herramientas respondan:

```powershell
nvim --version
git --version
gcc --version
```

---

## 2. Instalación de LazyVim

1. **Haz un respaldo de tu configuración actual de Neovim** si ya existía (paso seguro/opcional):

```powershell
Move-Item "$env:LOCALAPPDATA\nvim" "$env:LOCALAPPDATA\nvim.bak" -ErrorAction SilentlyContinue
Move-Item "$env:LOCALAPPDATA\nvim-data" "$env:LOCALAPPDATA\nvim-data.bak" -ErrorAction SilentlyContinue
```

2. **Clona la plantilla oficial de LazyVim** y elimina su historial `.git` para que puedas gestionar tu configuración libremente:

```powershell
git clone https://github.com/LazyVim/starter "$env:LOCALAPPDATA\nvim"
Remove-Item "$env:LOCALAPPDATA\nvim\.git" -Recurse -Force
```

---

## 3. Flujo diario para abrir un proyecto

Para que Neovim tome la raíz de tu proyecto y habilite las búsquedas correctamente, navega primero hasta la carpeta de tu código antes de ejecutarlo (ejemplo en el disco `D:`):

```powershell
D:
cd D:\Angular\28_dias_angular\03_introduccion\reto03
nvim .
```

*(La primera vez que ejecutes `nvim`, LazyVim descargará e instalará automáticamente todos sus plugins base).*

---

## 4. Configuración de Angular y TypeScript dentro de Neovim

Una vez dentro de Neovim (asegurándote de estar en **Modo Normal** presionando primero la tecla `Esc`):

### A. Instalar los parsers de sintaxis (Tree-sitter)

Ejecuta el siguiente comando para compilar el resaltado de sintaxis de TypeScript, TSX, Angular, HTML y SCSS:

```vim
:TSInstall typescript tsx angular html scss
```

Verifica que los parsers se hayan instalado y compilado correctamente usando `gcc` (revisa la sección **Installed languages** y confirma que no haya errores de `cl.exe` ni de target):

```vim
:checkhealth nvim-treesitter
```

Cierra la ventana de diagnóstico:

```vim
:q
```

### B. Activar el autocompletado y herramientas LSP (LazyExtras)

1. Abre el gestor de extras de LazyVim:

```vim
:LazyExtras
```

2. Busca con `/` (por ejemplo `/typescript` o `/angular`) y presiona **`Enter`**.
3. Presiona **`x`** sobre **`lang.typescript`** y **`lang.angular`** para activarlos.
4. Presiona **`q`** para salir de la ventana y reinicia Neovim (`:q` y vuelve a ejecutar `nvim .`) para que descargue e inicialice las herramientas correspondientes.

---

## 5. Guía rápida de comandos y atajos esenciales

### Comandos de salida y guardado (en Modo Normal, tras `Esc`)

* **`:w`** — Guardar el archivo actual.
* **`:q`** — Cerrar la ventana o buffer actual (cuando no hay cambios pendientes).
* **`:wq`** — Guardar los cambios y salir.
* **`:q!`** — Salir descartando cambios sin guardar (forzado).

### Atajos frecuentes en LazyVim (`Espacio` = tecla *Leader*)

* **`i`** — Entrar en modo escritura (*Insert*).
* **`Esc`** — Volver al Modo Normal.
* **`Espacio` + `e`** — Abrir, cerrar o enfocar el explorador lateral de archivos.
* **`f`** (en el dashboard) o **`Espacio` + `f` + `f`** — Buscar archivos por nombre en el proyecto.
* **`Espacio` + `s` + `g`** — Buscar texto o código dentro de todos los archivos del proyecto.
* **`Ctrl` + `s`** — Guardar el archivo actual (funciona tanto escribiendo como en Modo Normal).
* **`Espacio` + `q` + `q`** — Cerrar Neovim por completo.