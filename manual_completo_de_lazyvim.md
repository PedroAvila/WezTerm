# Manual Completo de LazyVim (Neovim)

> **Nota clave:** En LazyVim, la tecla `<leader>` (líder) es la **barra espaciadora (`Espacio`)**. Cuando veas una secuencia como `<leader>bd`, presiona **`Espacio`**, suéltalo, presiona **`b`**, suéltalo y presiona **`d`** (no las mantengas presionadas a la vez).

---

## 1. Modos de Trabajo en Neovim

Neovim funciona por modos. Si en algún momento te pierdes o escribes comandos sin querer, presiona **`Esc`** dos veces para volver al **Modo Normal**.

| Modo | Cómo entrar | Para qué sirve |
| :--- | :--- | :--- |
| **Normal** | `Esc` | Navegar por el código, ejecutar atajos, copiar, pegar y borrar. |
| **Inserción** | `i` (antes del cursor)<br>`a` (después del cursor)<br>`o` (nueva línea abajo)<br>`O` (nueva línea arriba) | Escribir código o texto normalmente. |
| **Visual** | `v` (por carácter)<br>`Shift + v` (por línea completa)<br>`Ctrl + v` (bloque vertical) | Seleccionar bloques de texto para copiar, comentar o borrar. |
| **Comandos** | `:` (en Modo Normal) | Ejecutar instrucciones como guardar (`:w`), salir (`:q`), abrir Mason (`:Mason`), etc. |

---

## 2. Guardar, Cerrar y Salir

| Acción | Atajo / Comando | Descripción |
| :--- | :--- | :--- |
| **Guardar archivo actual** | `Ctrl + s` o `:w` + `Enter` | Guarda los cambios del archivo activo. |
| **Guardar todos los archivos** | `:wa` + `Enter` | Guarda todos los archivos modificados abiertos. |
| **Cerrar solo la pestaña actual** | `<leader>bd` (`Espacio` + `b` + `d`) | Cierra el archivo actual sin romper tus ventanas ni el explorador. |
| **Cerrar pestaña sin guardar** | `:bd!` + `Enter` | Descarta los cambios y cierra el archivo actual. |
| **Cerrar todas menos la actual** | `<leader>bo` (`Espacio` + `b` + `o`) | Mantiene abierta solo la pestaña en la que estás parado. |
| **Salir de Neovim** | `<leader>qq` (`Espacio` + `q` + `q`) o `:qa` | Cierra todo el editor. |
| **Salir forzando (sin guardar)** | `:qa!` + `Enter` | Cierra Neovim descartando todos los cambios pendientes. |

---

## 3. Navegación entre Ventanas y Explorador (`Explorer`)

### Mover el foco entre ventanas y paneles
* **Mover foco a la izquierda (o ir al Explorer):** `Ctrl + h` (o `Ctrl + w` y luego `h` / `←`)
* **Mover foco a la derecha (volver al código):** `Ctrl + l` (o `Ctrl + w` y luego `l` / `→`)
* **Mover foco abajo / arriba entre ventanas:** `Ctrl + j` / `Ctrl + k` (o `Ctrl + w` y luego `j` / `k`)
* **Alternar a la siguiente ventana:** `Ctrl + w` + `w` o `<leader>ww` (`Espacio` + `w` + `w`)
* **Abrir / Enfocar / Cerrar Explorer:** `<leader>e` (`Espacio` + `e`)

### Acciones dentro del Explorer (panel izquierdo)
*(Asegúrate de haber presionado `Esc` si estabas en la barra naranja de búsqueda superior)*

| Tecla | Acción |
| :--- | :--- |
| `↑` / `↓` o `j` / `k` | Subir y bajar por archivos y carpetas. |
| `Enter` o `l` | Abrir archivo o desplegar carpeta. |
| `h` | Contraer carpeta actual. |
| `a` | **Crear archivo o carpeta** (si termina en `/`, crea carpeta; ej: `components/`). |
| `r` | **Renombrar** el archivo o carpeta seleccionada. |
| `d` | **Eliminar** el archivo o carpeta seleccionada. |
| `c` | Copiar archivo. |
| `p` | Pegar archivo copiado. |
| `y` | Copiar ruta del archivo. |
| `q` o `<leader>e` | Cerrar el panel del Explorer. |

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

| Acción | Atajo | Descripción |
| :--- | :--- | :--- |
| **Buscar y filtrar buffers abiertos** | `<leader>fb` (`Espacio` + `f` + `b`) | Lista interactiva para buscar y entrar a los buffers abiertos. |
| **Buscar archivo por nombre** | `<leader><space>` (`Espacio` + `Espacio`) o `<leader>ff` | Abre el buscador de archivos del proyecto. |
| **Buscar texto en todo el proyecto** | `<leader>/` (`Espacio` + `/`) o `<leader>sg` | Búsqueda global de texto (Live Grep / Ripgrep). |
| **Archivos recientes** | `<leader>fr` (`Espacio` + `f` + `r`) | Lista los archivos abiertos recientemente. |
| **Buscar palabra en archivo actual** | `/` + palabra + `Enter` (`n` sig., `N` ant.) | Búsqueda dentro del documento activo. |
| **Quitar resaltado de búsqueda** | `Esc` | Limpia los resaltados amarillos de la última búsqueda. |

---

## 7. Edición Rápida de Código (Modo Normal)

| Acción | Atajo |
| :--- | :--- |
| **Deshacer (Undo)** | `u` |
| **Rehacer (Redo)** | `Ctrl + r` |
| **Copiar línea completa** | `yy` |
| **Cortar / Borrar línea completa** | `dd` |
| **Pegar debajo / arriba** | `p` / `P` |
| **Mover línea abajo / arriba** | `Alt + j` / `Alt + k` |
| **Comentar / Descomentar línea** | `gcc` |
| **Comentar bloque seleccionado (Modo Visual)** | `gc` |
| **Formatear documento completo** | `<leader>cf` (`Espacio` + `c` + `f`) |
| **Seleccionar todo el archivo** | `ggVG` |

### Ejemplo práctico: Comentar un bloque de código

A continuación se muestra cómo comentar de forma ágil una función o bloque de varias líneas (por ejemplo, en TypeScript / Angular):

```typescript
onDeleteCharacter(index: number): void {
  this.characters.splice(index, 1);
}
```

#### Opción 1: Sombreando las 3 líneas (Visual Line)

1. **Asegúrate de estar en Modo Normal:** Presiona `Esc`.
2. **Navega hasta la función:** Baja 4 líneas hasta situarte en `onDeleteCharacter(index: number) : void {` (puedes escribir `4j` para saltar rápidamente).
3. **Activa el Modo Visual por línea:** Presiona `Shift + v` (`V`) para sombrear la línea completa actual.
4. **Extiende la selección:** Baja 2 líneas con `2j` (o `j` dos veces) hasta alcanzar la llave de cierre `}`.
5. **Comenta el bloque:** Presiona `gc`. Todo el bloque quedará comentado con `//` al instante:

```typescript
// onDeleteCharacter(index: number): void {
//   this.characters.splice(index, 1);
// }
```

> **Nota:** Para descomentar el bloque, simplemente vuelve a seleccionarlo en Modo Visual (`Shift + v` y `2j`) y presiona `gc` nuevamente.

#### Opción 2: Directamente desde Modo Normal (sin modo visual)
* Estando ubicado sobre la línea de `onDeleteCharacter(...)`, presiona `gc2j` (o `3gcc`) para comentar la línea actual y las 2 siguientes de forma instantánea.

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

## 9. Terminal Integrada

| Acción | Atajo |
| :--- | :--- |
| **Abrir / Ocultar terminal flotante** | `Ctrl + /` o `<leader>ft` |
| **Salir del modo escritura en la terminal** | `Ctrl + \` + `Ctrl + n` |
| **Cerrar terminal** | Escribir `exit` + `Enter` o `Ctrl + /` |

---

## 10. Gestión de Plugins, Lenguajes y Temas

### Comandos principales de mantenimiento
* **`:Lazy`** — Abre el gestor de plugins (presiona `U` para actualizar todos los plugins, `S` para sincronizar).
* **`:LazyExtras`** — Activa o desactiva soporte completo para lenguajes (ej. `lang.typescript`, `lang.angular`, `lang.json`) usando la tecla `x`.
* **`:Mason`** — Abre el gestor de servidores LSP, linters y formateadores (`i` para instalar, `u` para actualizar, `X` para desinstalar).
* **`:checkhealth`** — Diagnostica si falta alguna dependencia en Windows (Node.js, Git, Ripgrep, compilador C, etc.).

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