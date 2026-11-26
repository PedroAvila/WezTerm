# Manual Completo de LazyVim (Neovim)

Para abrir la configuración de LazyVim desde PowerShell:

```powershell
cd "$env:LOCALAPPDATA\nvim\lua"
```

> **Nota clave:** En LazyVim, la tecla `<leader>` (líder) es la **barra espaciadora (`Espacio`)**. Cuando veas una secuencia como `<leader>bd`, presiona **`Espacio`**, suéltalo, presiona **`b`**, suéltalo y presiona **`d`** (no las mantengas presionadas a la vez).

---

## 1. Modos de Trabajo en Neovim

Neovim funciona por modos. Si en algún momento te pierdes, escribes comandos sin querer o estás en modo Inserción, presiona **`Esc`** (o `Esc` dos veces) para volver al **Modo Normal**.

| Modo | Cómo entrar | Para qué sirve |
| :--- | :--- | :--- |
| **Normal** | `Esc` | Sale del modo Inserción (`-- INSERT --`) o cancela cuadros flotantes; navega por el código, ejecuta atajos, copia, pega y borra. |
| **Inserción** | `i` (antes del cursor)<br>`a` (después del cursor)<br>`o` (nueva línea abajo)<br>`O` (nueva línea arriba) | Escribir código o texto normalmente. |
| **Visual** | `v` (por carácter)<br>`Shift + v` (por línea completa)<br>`Ctrl + v` (bloque vertical) | Seleccionar bloques de texto para copiar, comentar o borrar. |
| **Comandos** | `:` (en Modo Normal) | Ejecutar instrucciones como guardar (`:w`), salir (`:q`), abrir Mason (`:Mason`), etc. |

---

## 2. Guardar, Cerrar y Salir

| Acción | Atajo / Comando | Descripción |
| :--- | :--- | :--- |
| **Guardar archivo actual** | `Ctrl + s` o `:w` + `Enter` | Guarda los cambios del archivo actual. |
| **Guardar y cerrar ventana** | `:wq` + `Enter` | Guarda el archivo actual y cierra la ventana. |
| **Guardar todos los archivos** | `:wa` + `Enter` | Guarda todos los archivos modificados abiertos. |
| **Guardar todo y salir de LazyVim** | `:wqa` + `Enter` | Guarda todos los archivos modificados y cierra LazyVim por completo. |
| **Cerrar solo la pestaña actual** | `<leader>bd` (`Espacio` + `b` + `d`) | Cierra el archivo actual sin romper tus ventanas ni el explorador. |
| **Cerrar pestaña sin guardar** | `:bd!` + `Enter` | Descarta los cambios y cierra el archivo actual. |
| **Cerrar todas menos la actual** | `<leader>bo` (`Espacio` + `b` + `o`) | Mantiene abierta solo la pestaña en la que estás parado. |
| **Salir de Neovim a PowerShell** | `<leader>qq` (`Espacio` + `q` + `q`) o `:qa` + `Enter` | Cierra todas las ventanas abiertas (incluyendo el panel lateral Explorer) y sale de LazyVim hacia PowerShell. |
| **Salir forzando (sin guardar)** | `:qa!` + `Enter` | Cierra Neovim descartando todos los cambios pendientes. |

---

## 3. Navegación entre Ventanas y Explorador (`Explorer`)

### Mover el foco entre ventanas y paneles
* **Mover foco a la izquierda (o ir al Explorer):** `Ctrl + h` (o `Ctrl + w` y luego `h` / `←`)
* **Mover foco a la derecha (volver al código):** `Ctrl + l` (o `Ctrl + w` y luego `l` / `→`)
* **Mover foco abajo / arriba entre ventanas:** `Ctrl + j` / `Ctrl + k` (o `Ctrl + w` y luego `j` / `k`)
* **Alternar a la siguiente ventana:** `Ctrl + w` + `w` o `<leader>ww` (`Espacio` + `w` + `w`)
* **Abrir / Enfocar / Cerrar Explorer:** `<leader>e` (`Espacio` + `e`) — Abre o cierra el panel lateral del explorador de archivos (Explorer) para alternar entre navegación y lectura/escritura a pantalla completa.

### Acciones y Filtrado dentro del Explorer (Snacks Explorer)

| Acción | Atajo / Tecla | Descripción |
| :--- | :--- | :--- |
| **Moverse por el árbol** | `↑` / `↓` o `j` / `k` | Subir y bajar por archivos y carpetas. |
| **Abrir o desplegar** | `Enter` o `l` | Abre el archivo seleccionado o expande/contrae una carpeta. |
| **Contraer carpeta** | `h` | Pliega la carpeta actual. |
| **Filtrar archivos en tiempo real** | `/` | Salta al cuadro de filtro superior (`>`) para filtrar archivos visibles. |
| **Navegar en lista filtrada** | `Ctrl + j` / `Ctrl + k` (o `↑` / `↓`) | Moverse entre los resultados del filtro y abrir el archivo deseado con `Enter`. |
| **Limpiar filtro y ver todo** | `Esc` (dos veces) | Sale del modo escritura del filtro y lo limpia para volver a ver todo el árbol. |
| **Crear archivo o carpeta** | `a` | Crea un nuevo archivo o carpeta (si termina en `/`) mediante el recuadro flotante *Add a new file or directory*. |
| **Renombrar** | `r` | Renombra el archivo o carpeta seleccionada. |
| **Eliminar** | `d` | Elimina el archivo o carpeta seleccionada. |
| **Copiar archivo** | `c` | Copia el archivo seleccionado. |
| **Pegar archivo** | `p` | Pega el archivo previamente copiado. |
| **Copiar ruta** | `y` | Copia la ruta del archivo al portapapeles. |
| **Cerrar Explorer** | `q` o `<leader>e` (`Espacio` + `e`) | Cierra el panel lateral del explorador para volver a pantalla completa. |

### Edición y Pegado en Cuadros Flotantes (Creación de Archivos)

Al presionar `a` dentro del Explorer, se abre el recuadro flotante de entrada (*Add a new file or directory*) en modo Inserción:

| Acción | Atajo / Combinación | Descripción |
| :--- | :--- | :--- |
| **Pegar desde el portapapeles de Windows** | `Ctrl + Shift + V` (o Clic derecho) | Pega texto desde el portapapeles de Windows dentro del recuadro flotante de creación de archivos en la terminal (Windows Terminal / WezTerm). |
| **Pegar portapapeles en modo Inserción** | `Ctrl + r` seguido de `+` | Pega el contenido del portapapeles del sistema (`+`) directamente dentro del modo Inserción o línea de entrada de Neovim. |
| **Salir o cancelar creación** | `Esc` | Sale del modo Inserción (`-- INSERT --`) y descarta el cuadro flotante, regresando al Modo Normal del Explorer. |

---

## 4. Navegación entre Pestañas y Buffers

> **Nota conceptual:** En Neovim, un **Buffer** representa un archivo abierto en memoria (mostrado en la barra de pestañas superior). Una **Ventana (Split)** es la división visible en pantalla donde visualizas el buffer.

En la barra superior aparecen tus archivos abiertos (`main.ts`, `app.ts`, etc.).

| Acción | Atajo | Descripción |
| :--- | :--- | :--- |
| **Buscar y entrar a buffers abiertos** | `<leader>fb` (`Espacio` + `f` + `b`) | Abre el selector interactivo (Telescope / Snacks / fzf) con vista previa para saltar rápidamente a cualquier archivo abierto. |
| **Selector rápido de buffers** | `<leader>,` (`Espacio` + `,`) | Acceso rápido al menú emergente para cambiar de buffer. |
| **Pestaña siguiente (derecha)** | `Shift + l` (`L`) o `]b` | Salta al buffer contiguo a la derecha. |
| **Pestaña anterior (izquierda)** | `Shift + h` (`H`) o `[b` | Salta al buffer contiguo a la izquierda. |
| **Alternar entre los 2 últimos archivos** | `<leader>bb` (`Espacio` + `b` + `b`) o `<leader>\`` | Vuelve de inmediato al archivo editado anteriormente. |
| **Cerrar buffer actual** | `<leader>bd` (`Espacio` + `b` + `d`) | Cierra el archivo actual sin romper las ventanas divididas. |
| **Cerrar todos menos el actual** | `<leader>bo` (`Espacio` + `b` + `o`) | Cierra el resto de buffers y conserva el activo. |
| **Fijar / Desfijar pestaña (Pin)** | `<leader>bp` (`Espacio` + `b` + `p`) | Fija el buffer para que no se cierre automáticamente. |

---

## 5. División de Pantalla y Gestión de Ventanas (Splits)

| Acción | Atajo | Descripción |
| :--- | :--- | :--- |
| **Dividir pantalla verticalmente** | `<leader>\|` o `<leader>w\|` (`Espacio` + `\|`) | Divide la ventana actual en dos paneles verticales (`:vsplit`). |
| **Dividir pantalla horizontalmente** | `<leader>-` o `<leader>w-` (`Espacio` + `-`) | Divide la ventana actual en dos paneles horizontales (`:split`). |
| **Moverse entre ventanas** | `Ctrl + h` / `j` / `k` / `l` | Salta el foco a la ventana izquierda, abajo, arriba o derecha. |
| **Alternar ventana activa** | `Ctrl + w` + `w` o `<leader>ww` | Mueve el foco a la siguiente ventana abierta. |
| **Cerrar solo la ventana actual** | `<leader>wd` o `Ctrl + w` + `c` | Cierra la división actual (`:close`). |
| **Cerrar las demás ventanas** | `Ctrl + w` + `o` | Mantiene solo la ventana activa y cierra todas las demás divisiones (`:only`). |
| **Igualar tamaño de divisiones** | `Ctrl + w` + `=` | Restablece todas las divisiones a dimensiones iguales. |
| **Ajustar altura de ventana** | `Ctrl + ↑` / `Ctrl + ↓` | Incrementa o reduce la altura de la división activa. |
| **Ajustar anchura de ventana** | `Ctrl + ←` / `Ctrl + →` | Incrementa o reduce la anchura de la división activa. |
| **Rotar posición de ventanas** | `Ctrl + w` + `r` | Rota la disposición de los paneles en pantalla. |
| **Intercambiar ventana** | `Ctrl + w` + `x` | Intercambia la ventana actual de posición con la contigua. |

---

## 6. Búsqueda Rápida de Archivos y Texto

### Búsqueda Global en el Proyecto (Archivos y Texto)

| Acción | Atajo / Comando | Descripción |
| :--- | :--- | :--- |
| **Buscador global de archivos** | `<leader><space>` (`Espacio` + `Espacio`) o `<leader>ff` | Abre el buscador global de archivos en todas las carpetas y subcarpetas del proyecto. |
| **Buscar texto en todo el proyecto** | `<leader>/` (`Espacio` + `/`) o `<leader>sg` | Búsqueda global de palabras o cadenas en todos los archivos a la vez (Live Grep / Ripgrep). |
| **Buscar y filtrar buffers abiertos** | `<leader>fb` (`Espacio` + `f` + `b`) | Lista interactiva para buscar y saltar entre los archivos cargados en memoria. |
| **Archivos recientes** | `<leader>fr` (`Espacio` + `f` + `r`) | Lista y filtra los archivos abiertos recientemente. |

### Buscar Palabras dentro de un Archivo (Equivalente a Ctrl + F)

| Acción | Atajo / Comando | Descripción |
| :--- | :--- | :--- |
| **Iniciar búsqueda hacia adelante** | `/` (en Modo Normal) + palabra + `Enter` | Escribe el término y presiona `Enter` para buscar hacia adelante desde el cursor. |
| **Iniciar búsqueda hacia atrás** | `?` (en Modo Normal) + palabra + `Enter` | Busca ocurrencias hacia atrás en el archivo. |
| **Siguiente coincidencia** | `n` | Salta a la siguiente coincidencia encontrada. |
| **Anterior coincidencia** | `N` | Salta a la coincidencia anterior. |
| **Ignorar mayúsculas y minúsculas** | `/\c` + palabra + `Enter` | Búsqueda insensible a mayúsculas/minúsculas (ej: `/\cguardar` halla `Guardar`, `GUARDAR`, `guardar`). |
| **Quitar resaltado de búsqueda** | `Esc` o `:noh` + `Enter` | Limpia los resaltados amarillos de los resultados en pantalla (`:nohlsearch`). |

---

## 7. Edición Rápida de Código y Operaciones sobre Archivos

### Atajos Generales de Edición (Modo Normal)

| Acción | Atajo / Comando | Descripción |
| :--- | :--- | :--- |
| **Deshacer (Undo)** | `u` | Revierte el último cambio realizado. |
| **Rehacer (Redo)** | `Ctrl + r` | Rehace el cambio revertido. |
| **Copiar línea completa** | `yy` | Copia la línea actual al registro interno. |
| **Cortar / Borrar línea completa** | `dd` | Corta la línea actual. |
| **Pegar debajo / arriba** | `p` / `P` | Pega el contenido copiado debajo o arriba del cursor. |
| **Mover línea abajo / arriba** | `Alt + j` / `Alt + k` | Desplaza verticalmente la línea o bloque actual. |
| **Comentar / Descomentar línea** | `gcc` | Alterna el comentario en la línea actual. |
| **Comentar bloque seleccionado** | `gc` | Comenta el bloque sombreado en Modo Visual. |
| **Pegar portapapeles en Inserción** | `Ctrl + r` seguido de `+` | Pega el contenido del portapapeles de Windows directamente desde el Modo Inserción de Neovim. |
| **Formatear documento completo** | `<leader>cf` (`Espacio` + `c` + `f`) | Formatea el archivo activo mediante el formateador LSP (Prettier, etc.). |

### Seleccionar, Copiar y Borrar Todo un Archivo

Existen dos maneras eficientes de operar sobre la totalidad de un archivo:

#### Método 1: Selección Visual Interactiva
1. **`ggVG`**: Presiona `gg` (ir al inicio del archivo), `Shift + v` / `V` (activar modo visual por líneas) y `G` (extender la selección hasta el final).
2. Con todo el archivo seleccionado:
   * **`y`**: Copia todo el contenido al registro interno de Neovim.
   * **`"+y`**: Copia todo el contenido directamente al **portapapeles de Windows** (listo para pegar con `Ctrl + V` en cualquier otra aplicación).
   * **`d`**: Borra (corta) todo el contenido del archivo.

#### Método 2: Comandos Rápidos Directos (Modo Comandos)
Sin necesidad de seleccionar manualmente el texto:
* **`:%y` + `Enter`**: Copia todo el archivo al registro interno de Neovim.
* **`:%y+` + `Enter`**: Copia todo el archivo directamente al portapapeles de Windows.
* **`:%d` + `Enter`**: Borra todo el contenido del archivo al instante.

### Ejemplo práctico: Comentar un bloque de código

A continuación se muestra cómo comentar de forma ágil una función o bloque de varias líneas (por ejemplo, en TypeScript / Angular):

```typescript
onDeleteCharacter(index: number): void {
  this.characters.splice(index, 1);
}
```

#### Opción 1: Sombreando las 3 líneas (Visual Line)
1. **Asegúrate de estar en Modo Normal:** Presiona `Esc`.
2. **Navega hasta la función:** Sitúate sobre `onDeleteCharacter(index: number): void {`.
3. **Activa el Modo Visual por línea:** Presiona `Shift + v` (`V`).
4. **Extiende la selección:** Baja 2 líneas con `2j` (o `j` dos veces) hasta la llave de cierre `}`.
5. **Comenta el bloque:** Presiona `gc`. Todo el bloque quedará comentado con `//` al instante:

```typescript
// onDeleteCharacter(index: number): void {
//   this.characters.splice(index, 1);
// }
```

> **Nota:** Para descomentar el bloque, simplemente vuelve a seleccionarlo en Modo Visual (`Shift + v` y `2j`) y presiona `gc` nuevamente.

#### Opción 2: Directamente desde Modo Normal (sin modo visual)
* Estando ubicado sobre la línea de `onDeleteCharacter(...)`, presiona `gc2j` (o `3gcc`) para comentar la línea actual y las 2 siguientes de forma instantánea.

### Ejemplo práctico: Copiar una palabra específica dentro de una línea

En **Modo Normal** (asegúrate de no estar en Modo Inserción — presiona `Esc` si ves el cursor de inserción), teniendo el cursor en cualquier parte de una línea como:

```html
(keyup.enter)="addTodo()"
```

Si quieres copiar únicamente el nombre del método `addTodo`:

#### Opción 1: Forma más rápida (`f` + `y` + `w`)
1. Presiona `f` y luego `a` para saltar directo a la `a` de `addTodo` dentro de la misma línea.
2. Presiona `yw` para copiar `addTodo`.

> **Nota:** `f<carácter>` busca hacia adelante en la línea actual hasta la primera coincidencia del carácter indicado (`a`), y `yw` (*yank word*) copia la palabra desde el cursor hasta el límite antes de `()`.

#### Opción 2: Usar la búsqueda (`/`)
1. Presiona `/addTodo` y luego `Enter` para colocar el cursor al inicio de `addTodo`.
2. Presiona `yw` para copiar la palabra.

---

## 8. Inteligencia de Código (LSP: TypeScript, Angular, HTML)

Cuando estás sobre una variable, función o componente:

| Acción | Atajo |
| :--- | :--- |
| **Ir a la definición** | `gd` |
| **Ver referencias de uso** | `gr` |
| **Ver documentación / tipo al pasar** | `Shift + k` (`K`) |
| **Renombrar símbolo en todo el proyecto** | `<leader>cr` (`Espacio` + `c` + `r`) |
| **Acciones rápidas / Auto-importar** | `<leader>ca` (`Espacio` + `c` + `a`) |
| **Ver errores y advertencias del archivo** | `<leader>xx` (`Espacio` + `x` + `x`) |
| **Siguiente / Anterior error** | `]d` / `[d` |
| **Ver estado de servidores LSP activos** | `:LspInfo` + `Enter` |

---

## 9. Terminal Integrada y Navegación entre Paneles

Neovim incluye terminales integradas para ejecutar comandos de PowerShell sin abandonar el editor.

| Acción | Atajo / Comando | Descripción |
| :--- | :--- | :--- |
| **Abrir / Ocultar terminal flotante** | `Ctrl + /` o `<leader>ft` | Abre o esconde una ventana flotante de PowerShell. |
| **Salir del modo escritura en la terminal** | `Ctrl + \` y luego `Ctrl + n` | Pasa la terminal a Modo Normal para poder navegar o saltar a otros paneles. |
| **Pasar de la consola al Explorer** | `Ctrl + w` + `h` (o `Ctrl + h`) | Mueve el foco desde la terminal hacia el panel izquierdo (Explorer o split contiguo). |
| **Pasar del Explorer / editor a la consola** | `Ctrl + w` + `j` (o `Ctrl + j`) | Mueve el foco hacia la consola situada abajo. |
| **Reactivar la escritura en la consola** | `i` (o `a`) | Vuelve a activar el modo interactivo para escribir comandos en la terminal. |
| **Cerrar terminal** | Escribir `exit` + `Enter` o `Ctrl + /` | Finaliza la sesión de shell o cierra la terminal flotante. |

---

## 10. Corrector Ortográfico (Rayas Rojas y Spellcheck)

Las rayas rojas onduladas debajo de las palabras indican que el corrector ortográfico (*spellcheck*) de Neovim está detectando un posible error de escritura. Puedes activarlo, configurarlo o deshabilitarlo fácilmente.

| Acción | Atajo / Comando | Descripción |
| :--- | :--- | :--- |
| **Activar / Desactivar rayas rojas (temporal)** | `<leader>us` (`Espacio` + `u` + `s`) o `:set spell!` | Alterna el corrector ortográfico en el archivo actual. |
| **Desactivar corrector en archivo actual** | `:set nospell` + `Enter` | Quita de inmediato el subrayado rojo en el archivo activo. |
| **Activar corrección en inglés y español** | `:set spelllang=en,es` + `Enter` | Permite que el corrector valide palabras tanto en inglés como en español simultáneamente. |
| **Abrir buscador de archivos de configuración** | `<leader>fc` (`Espacio` + `f` + `c`) | Atajo directo para buscar y abrir archivos de configuración (`options.lua`, etc.). |

### Desactivar el subrayado ortográfico permanentemente

Si prefieres trabajar sin corrector ortográfico en todos tus proyectos:

1. Presiona `<leader>fc` (`Espacio` + `f` + `c`) y selecciona `options.lua` (o abre directamente el archivo `$env:LOCALAPPDATA\nvim\lua\config\options.lua`).
2. Agrega la siguiente opción de configuración:

```lua
-- Desactivar el corrector ortográfico permanentemente (sin rayas rojas)
vim.opt.spell = false
```

3. Guarda con `Ctrl + s`. Neovim aplicará el ajuste inmediatamente.

---

## 11. Gestión de Plugins, Lenguajes y Temas

### Comandos principales de mantenimiento
* **`:Lazy`** — Abre el gestor de plugins (presiona `U` para actualizar todos los plugins, `S` para sincronizar).
* **`:LazyExtras`** — Abre el menú de extras oficiales de LazyVim para activar o desactivar soporte extendido de lenguajes y herramientas (ej. `lang.typescript`, `lang.angular`, `lang.markdown`) presionando `x`.
* **`:Mason`** — Abre el gestor de servidores LSP, linters y formateadores (`i` para instalar, `u` para actualizar, `X` para desinstalar).
* **`:checkhealth`** — Diagnostica si falta alguna dependencia en Windows (Node.js, Git, Ripgrep, compilador C, etc.).

### Visualización y Renderizado de Markdown (`lang.markdown`)

Al habilitar `lang.markdown` en `:LazyExtras` (presionando `x`), LazyVim activa el soporte avanzado para archivos `.md` con renderizado en el editor y vista previa en el navegador:

| Acción | Atajo / Comando | Descripción |
| :--- | :--- | :--- |
| **Menú de LazyExtras** | `:LazyExtras` + `Enter` | Abre el menú de extras oficiales de LazyVim (donde activas `lang.markdown` presionando `x` para habilitar el renderizado de tablas, títulos y listas). |
| **Alternar renderizado visual en editor** | `<leader>um` (`Espacio` + `u` + `m`) | Activa o desactiva el renderizado visual de Markdown dentro del editor (Modo Normal) para alternar entre escritura limpia en texto plano y vista formateada. |
| **Vista previa en el navegador web** | `<leader>cp` (`Espacio` + `c` + `p`) o `:MarkdownPreview` | Abre una vista previa renderizada en tiempo real del archivo `.md` en tu navegador web. |

### Estructura de carpetas de configuración en Windows
Tu configuración vive en `%LOCALAPPDATA%\nvim\` (`C:\Users\TuUsuario\AppData\Local\nvim\`):

```text
nvim/
├── init.lua                 # Punto de entrada principal
├── lazyvim.json             # Registro de LazyExtras activados
└── lua/
    ├── config/
    │   ├── keymaps.lua      # Tus atajos de teclado personalizados
    │   ├── lazy.lua         # Configuración del gestor lazy.nvim
    │   └── options.lua      # Opciones de Neovim (números de línea, tabulación, etc.)
    └── plugins/
        └── colorscheme.lua  # Archivos donde agregas plugins o temas personalizados
```

### Abrir y editar la configuración desde PowerShell

Para navegar directamente a la carpeta donde residen tus archivos de configuración (`config/`, `plugins/`, etc.) desde PowerShell:

```powershell
cd "$env:LOCALAPPDATA\nvim\lua"
```

> **Consejo práctico:**
> * Una vez dentro de esa carpeta, puedes abrir la configuración completa en Neovim ejecutando:
>   ```powershell
>   nvim .
>   ```
> * O puedes abrir directamente la configuración sin cambiar de directorio con:
>   ```powershell
>   nvim "$env:LOCALAPPDATA\nvim\lua"
>   ```
> * Dentro de Neovim, también puedes presionar `<leader>fc` (`Espacio` + `f` + `c`) para buscar y abrir cualquier archivo de configuración rápidamente.

### Ejemplo: Configurar Tema Estilo Sublime Text 4 (`lua/plugins/colorscheme.lua`)

```lua
return {
  {
    "loctvl842/monokai-pro.nvim",
    lazy = false,
    priority = 1000,
    opts = {
      filter = "classic", -- Opciones: "classic", "octagon", "pro", "machine", "ristretto", "spectrum"
    },
  },
  {
    "LazyVim/LazyVim",
    opts = {
      colorscheme = "monokai-pro",
    },
  },
}
```

---

## 12. Gestión de la Ventana de la Terminal en Windows con el Teclado

Atajos del sistema operativo Windows 11 y emuladores de terminal (Windows Terminal / WezTerm) para organizar, desplazar y redimensionar ventanas sin levantar las manos del teclado:

| Acción | Atajo de Teclado | Descripción |
| :--- | :--- | :--- |
| **Acoplar a mitad izquierda / derecha** | `Win` (⊞) + `←` / `Win` (⊞) + `→` | Acopla la ventana de la terminal exactamente en la mitad izquierda o derecha de la pantalla (*Snap Assist*). |
| **Maximizar, minimizar o cuartos de pantalla** | `Win` (⊞) + `↑` / `Win` (⊞) + `↓` | Maximiza la ventana (`Win + ↑`), la restaura o minimiza (`Win + ↓`), o la ajusta a un cuarto de pantalla. |
| **Mover ventana entre monitores** | `Win` (⊞) + `Shift` + `←` / `→` | Traslada la ventana directamente a la pantalla contigua conservando sus dimensiones. |
| **Mover ventana libremente con teclado** | `Alt` + `Barra espaciadora`, luego `M`, flechas (`←` `↑` `↓` `→`) y `Enter` | Abre el menú de control de ventana de Windows, activa el modo mover (`M`), desplaza la ventana con las flechas y confirma con `Enter`. |
| **Desplegar / Ocultar modo Quake** | `Win` (⊞) + `Alt` + `º` | Despliega u oculta la terminal en modo desplegable superior rápido (ventana emergente *Quake* en Windows Terminal). |

---

## 13. Configuración Personalizada Estilo *devaslife* en Windows

> **Nota importante:** Esta sección documenta la configuración inspirada en *devaslife* (Takuya Matsuyama) adaptada a **Windows**. Se mantiene separada de los atajos predeterminados de LazyVim (secciones 4–8) porque sobrescribe teclas estándar en `lua/config/keymaps.lua` (como `dw`, `ss`/`sv`, `sh`/`sj`/`sk`/`sl`, `<C-a>` o `<Tab>`). Si utilizas esta configuración, estos atajos reemplazan o complementan a los valores por defecto.

### 13.1 Estructura y Rutas en Windows

En los tutoriales de macOS/Linux suele aparecer `~/.config/nvim`. En Windows, tu directorio principal de configuración es `%LOCALAPPDATA%\nvim`.

```powershell
cd "$env:LOCALAPPDATA\nvim"
```

Archivos clave dentro de esta configuración:

* `init.lua`: Punto de entrada que carga `lazy.nvim` y tus configuraciones.
* `lua/config/keymaps.lua`: Tus atajos de teclado personalizados.
* `lua/config/options.lua`: Opciones generales del editor.
* `lua/config/autocmds.lua`: Autocomandos.
* `lua/plugins/colorscheme.lua`: Configuración de tema visual (por ejemplo, `solarized-osaka.nvim`).

### 13.2 Herramientas de Búsqueda en Terminal (`fd` y `rg`)

Instaladas mediante `winget` para búsquedas rápidas desde PowerShell y como motor para búsquedas dentro de LazyVim:

| Herramienta / Comando | Uso en PowerShell | Equivalente en LazyVim | Descripción |
| :--- | :--- | :--- | :--- |
| **`fd <patrón>`** | `fd lua` | `<leader>ff` o `<leader><space>` | Busca **archivos y carpetas por su nombre** (en el ejemplo, lista rutas relacionadas con `lua`). |
| **`rg <texto>`** (*ripgrep*) | `rg lazy` | `<leader>sg` o `<leader>/` | Busca **texto dentro del contenido de los archivos** mostrando archivo y número de línea. |

### 13.3 Atajos Configurados en `lua/config/keymaps.lua`

La mayoría de estos atajos están mapeados en **Modo Normal (`"n"`)** con `{ noremap = true, silent = true }`:

#### Edición, Selección, Números y Jumplist

| Categoría | Atajo | Acción / Mapeo | Descripción |
| :--- | :--- | :--- | :--- |
| **Números** | `+` | `<C-a>` | Incrementa el número bajo el cursor. |
| **Números** | `-` | `<C-x>` | Decrementa el número bajo el cursor. |
| **Borrado** | `dw` | `vb_d` | Borra una palabra hacia atrás. |
| **Selección** | `<C-a>` | `gg<S-v>G` | Selecciona todo el buffer. *(Nota: en algunas terminales de Windows conviene revisar si `<C-a>` es interceptado por el sistema o usar `<leader>a`).* |
| **Jumplist** | `<C-m>` | `<C-i>` | Salta hacia adelante en la lista de saltos. |

#### Pestañas (Tabs), Ventanas (Splits) y Redimensionado

| Categoría | Atajo | Acción / Mapeo | Descripción |
| :--- | :--- | :--- | :--- |
| **Pestañas** | `te` | `:tabedit` | Abre una nueva pestaña. |
| **Pestañas** | `<Tab>` | `:tabnext<Return>` | Cambia a la siguiente pestaña. |
| **Pestañas** | `<S-Tab>` | `:tabprev<Return>` | Cambia a la pestaña anterior. |
| **Splits** | `ss` | `:split<Return>` | Divide la ventana en horizontal. |
| **Splits** | `sv` | `:vsplit<Return>` | Divide la ventana en vertical. |
| **Navegación** | `sh` | `<C-w>h` | Mueve el foco a la ventana de la **izquierda**. |
| **Navegación** | `sk` | `<C-w>k` | Mueve el foco a la ventana de **arriba**. |
| **Navegación** | `sj` | `<C-w>j` | Mueve el foco a la ventana de **abajo**. |
| **Navegación** | `sl` | `<C-w>l` | Mueve el foco a la ventana de la **derecha**. |
| **Redimensionar** | `<C-w><Left>` | `<C-w><` | Reduce el ancho de la ventana. |
| **Redimensionar** | `<C-w><Right>` | `<C-w>>` | Aumenta el ancho de la ventana. |
| **Redimensionar** | `<C-w><Up>` | `<C-w>+` | Aumenta el alto de la ventana. |
| **Redimensionar** | `<C-w><Down>` | `<C-w>-` | Reduce el alto de la ventana. |

#### Diagnósticos (LSP)

* **`<C-j>`**: Salta al siguiente diagnóstico mostrando una ventana flotante:

```lua
vim.diagnostic.jump({ count = 1, float = true })
```

### 13.4 Operaciones Rápidas de Edición y Ventanas

* **Duplicar una línea (Modo Normal):** `yyp` (copia la línea actual y la pega debajo).
* **Duplicar un bloque de líneas:** `Shift + v` para seleccionar líneas, moverse con `j`/`k` (o flechas), luego `y` para copiar y `p` para pegar.

| Acción | Atajo / Comando | Descripción |
| :--- | :--- | :--- |
| **Dejar solo la ventana activa** | `:only` | Cierra las demás divisiones y mantiene únicamente la ventana actual. |
| **Guardar archivo actual** | `:w` | Guarda los cambios del archivo activo. |
| **Cerrar todo y salir** | `:qa` | Cierra todas las ventanas/pestañas y sale de Neovim. |
| **Salir sin guardar** | `:qa!` | Sale de Neovim forzadamente descartando cambios. |
| **Cerrar ventanas flotantes** | `Esc` o `q` | Cierra cuadros flotantes de documentación, ayuda o reportes. |

### 13.5 Verificación de Diagnóstico, LSP y Gestión de Plugins

| Herramienta / Acción | Comando o Atajo | Descripción |
| :--- | :--- | :--- |
| **Estado del LSP (ej. `lua_ls`)** | `:checkhealth lsp` | Verifica la salud de los servidores LSP (presiona `q` para salir de la ventana). |
| **Gestor de servidores/herramientas** | `:Mason` | Abre Mason para instalar servidores LSP, linters o formateadores (presiona `i` sobre un paquete para instalarlo). |
| **Gestor de plugins (`lazy.nvim`)** | `:Lazy` o `<leader>l` | Abre el panel de plugins (`U` para actualizar o `q` para salir). |
| **Explorar atajos activos** | `<leader>sk` | Abre el buscador para inspeccionar todos los keymaps cargados actualmente. |

### 13.6 Uso de Telescope y File Browser (Estilo *devaslife*)

Esta configuración personalizada de [`nvim-telescope/telescope.nvim`](https://github.com/nvim-telescope/telescope.nvim) junto con [`telescope-file-browser.nvim`](https://github.com/nvim-telescope/telescope-file-browser.nvim) replica el flujo de trabajo rápido de *devaslife* (por ejemplo, guardado en `$env:LOCALAPPDATA\nvim\lua\plugins\editor.lua` o `telescope.lua`).

> **Importante sobre requisitos en LazyVim:**
> * Esta configuración carga la extensión `"fzf"` (`require("telescope").load_extension("fzf")`) y usa `live_grep` con `ripgrep` (`rg`). Asegúrate de tener activo el extra `editor.telescope` en `:LazyExtras` (o declarado `telescope-fzf-native.nvim` en tus plugins) para evitar errores al iniciar Telescope.
> * En esta configuración, la tecla **`;`** funciona como prefijo rápido de búsqueda (en lugar de esperar `<leader>`). Al presionar `;`, Neovim aguardará brevemente la segunda tecla (`f`, `r`, `t`, `;`, `e` o `s`).

#### Atajos principales de Telescope (Modo Normal)

| Atajo | Secuencia | Función de Telescope | Cómo se usa en la práctica |
| :--- | :--- | :--- | :--- |
| **`;f`** | `;` luego `f` | `find_files` | Busca **archivos por nombre** en el proyecto actual. Incluye archivos ocultos (`.env`, `.gitignore`, etc.), pero respeta lo ignorado por `.gitignore`. |
| **`;r`** | `;` luego `r` | `live_grep` | Busca **texto o código en tiempo real** dentro de todo el proyecto (usa `ripgrep`). Escribe la palabra y verás archivo, línea y vista previa al instante. |
| **`\\`** | `\` dos veces | `buffers` | Lista únicamente los **archivos (buffers) abiertos** en memoria para cambiar rápidamente entre ellos. |
| **`;t`** | `;` luego `t` | `help_tags` | Busca en la **documentación oficial de Neovim y plugins** (útil para consultar comandos o configuración de Lua). |
| **`;;`** | `;` dos veces | `resume` | **Reanuda la última búsqueda** de Telescope exactamente donde la dejaste (conserva el texto que escribiste y el resultado seleccionado). |
| **`;e`** | `;` luego `e` | `diagnostics` | Muestra los **errores y advertencias del LSP** en un panel inferior compacto (tema `ivy`). Se abre directamente en **Modo Normal** y sin vista previa para leer la lista completa con claridad. |
| **`;s`** | `;` luego `s` | `treesitter` | Lista los **símbolos del archivo actual** (funciones, clases, métodos, interfaces, variables) detectados por Tree-sitter para saltar directo a ellos. |
| **`sf`** | `s` luego `f` | `file_browser` | Abre el **explorador de archivos de Telescope** posicionado en la **carpeta del archivo actual**. |
| **`<leader>fP`** | `Espacio`, `f`, `Shift + p` | `find_files` (plugins) | Busca archivos directamente dentro de la **carpeta de plugins instalados** por `lazy.nvim` (útil para revisar código fuente de plugins). |

#### Comportamiento visual de las ventanas de Telescope

Con las opciones configuradas en `opts.defaults`:
* **Barra de búsqueda arriba (`prompt_position = "top"`):** El cuadro para escribir aparece en la parte superior y los mejores resultados se ordenan hacia abajo (`sorting_strategy = "ascending"`).
* **Ajuste de líneas largas (`wrap_results = true`):** Si una ruta o línea de resultado es muy larga, se envuelve en múltiples líneas en lugar de cortarse.
* **Reemplazo de `netrw` (`hijack_netrw = true`):** Si abres una carpeta directamente (por ejemplo `nvim .` desde PowerShell o `:e .`), Neovim abrirá `telescope-file-browser` en lugar del explorador clásico `netrw`.

#### Cómo usar el Explorador de Archivos (`sf`) paso a paso

A diferencia de `;f` o `;r` (que abren listos para escribir), **`sf` se abre en Modo Normal (`initial_mode = "normal"`)**, sin vista previa (`previewer = false`), mostrando archivos ocultos (`hidden = true`), incluyendo archivos ignorados por Git (`respect_gitignore = false`) y agrupando primero las carpetas (`grouped = true`).

Si presionas letras nada más abrir `sf`, no escribirás en el buscador: ejecutarás acciones de navegación. Úsalo así:

| Acción dentro de `sf` | Tecla / Atajo | Descripción |
| :--- | :--- | :--- |
| **Moverse por la lista** | `j` / `k` o `↓` / `↑` | Baja o sube entre carpetas y archivos. |
| **Salto rápido hacia arriba** | `Ctrl + u` | Sube **10 posiciones** de golpe en la lista (mapeo personalizado). |
| **Abrir archivo o entrar a carpeta** | `Enter` | Abre el archivo seleccionado en el editor o entra en la carpeta seleccionada. |
| **Subir a la carpeta padre** | `h` | Retrocede un nivel hacia la carpeta superior (`..`). |
| **Filtrar escribiendo** | `/` | Cambia a **Modo Inserción** para escribir en la barra superior y filtrar la carpeta actual. Presiona `Esc` para volver al Modo Normal. |
| **Crear archivo o carpeta** | `N` (`Shift + n`) | Abre el recuadro para crear un elemento en la carpeta actual: escribe `archivo.ts` para un archivo o `carpeta/` (terminado en `/`) para crear un directorio, y confirma con `Enter`. |
| **Desplazar vista previa** | `PageUp` / `PageDown` | Sube o baja el contenido de la vista previa (en vistas donde el previewer esté habilitado). |
| **Cerrar el explorador** | `Esc` (en Modo Normal) o `q` | Cierra `telescope-file-browser` y regresa al código sin hacer cambios. |

> **Flujo típico recomendado con esta configuración:**
> 1. Presiona `;f` para saltar rápido a cualquier archivo del proyecto por nombre.
> 2. Presiona `;r` para buscar una función o texto específico en todo el código.
> 3. Si cerraste el buscador y quieres volver al mismo resultado, presiona `;;`.
> 4. Si necesitas crear un archivo hermano junto al archivo que estás editando, presiona `sf`, luego `N`, escribe el nombre y pulsa `Enter`.
> 5. Si quieres revisar errores del proyecto sin usar el ratón, presiona `;e`, muévete con `j`/`k` y pulsa `Enter` para ir directo a la línea del error.
