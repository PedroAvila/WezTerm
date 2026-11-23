# 🚀 Manual de WezTerm - Configuración Personalizada

Esta configuración reemplaza el uso del "Leader" tradicional por combinaciones directas usando `Ctrl + Alt`, lo que hace que los atajos sean más rápidos y evita conflictos con el sistema operativo Windows o el software del teclado.

**La regla de oro:** Para cualquier atajo, mantén presionado `Ctrl` y `Alt` al mismo tiempo, y luego pulsa la tecla de la acción.

---

## 🪟 1. Gestión de Paneles (Splits)

| Acción | Atajo de Teclado | Descripción |
| :--- | :--- | :--- |
| **Dividir a la derecha** | `Ctrl` + `Alt` + `D` | Crea un panel nuevo al lado derecho (D de Derecha). |
| **Dividir hacia abajo** | `Ctrl` + `Alt` + `S` | Crea un panel nuevo debajo (S de Split). |
| **Navegar entre paneles** | `Ctrl` + `Alt` + `Flechas` (⬅️ ⬆️ ⬇️ ➡️) | Mueve el foco al panel que elijas. |
| **Cerrar el panel actual** | `Ctrl` + `Alt` + `X` | Cierra el panel donde estás (pedirá confirmación). |
| **Hacer Zoom a un panel** | `Ctrl` + `Alt` + `Z` | Expande el panel actual a pantalla completa temporalmente. |
| **Redimensionar paneles** | `Ctrl` + `Alt` + `H`/`J`/`K`/`L` | Ajusta el tamaño (Izquierda, Abajo, Arriba, Derecha). |

---

## 📑 2. Gestión de Pestañas (Tabs)

| Acción | Atajo de Teclado | Descripción |
| :--- | :--- | :--- |
| **Nueva pestaña** | `Ctrl` + `Alt` + `C` | Abre una pestaña nueva en el mismo directorio. |
| **Cerrar pestaña** | `Ctrl` + `Alt` + `Shift` + `&` | Cierra la pestaña actual. |
| **Siguiente pestaña** | `Ctrl` + `Alt` + `N` | Va a la pestaña de la derecha. |
| **Pestaña anterior** | `Ctrl` + `Alt` + `P` | Va a la pestaña de la izquierda. |
| **Saltar a pestaña 1, 2, 3...** | `Ctrl` + `Alt` + `1`, `2`, `3`... | Salta directamente a esa pestaña por su número. |

---

## 💡 3. Atajos Nativos de WezTerm (Muy útiles)

WezTerm trae atajos por defecto que no requieren configuración y son excelentes para el día a día:

| Acción | Atajo de Teclado |
| :--- | :--- |
| **Menú de Comandos** | `Ctrl` + `Shift` + `P` (Tu salvavidas si olvidas algo) |
| **Nueva pestaña (estándar)** | `Ctrl` + `Shift` + `T` |
| **Cerrar pestaña (estándar)** | `Ctrl` + `Shift` + `W` |
| **Buscar texto en pantalla** | `Ctrl` + `Shift` + `F` |
| **Copiar / Pegar** | `Ctrl` + `Shift` + `C` / `Ctrl` + `Shift` + `V` |
| **Aumentar / Reducir fuente** | `Ctrl` + `+` / `Ctrl` + `-` |
| **Pantalla completa** | `Alt` + `Enter` |

---

## 🎨 4. Características de la Configuración Actual

*   **Fuente:** `JetBrainsMono Nerd Font Mono` (tamaño 11).
*   **Tema:** `Catppuccin Mocha` (colores oscuros y suaves).
*   **Transparencia:** 85% de opacidad con efecto *Acrylic* (cristal esmerilado) en Windows.
*   **Shell por defecto:** PowerShell (en lugar del clásico CMD).
*   **Barra de pestañas:** Oculta cuando solo hay una pestaña abierta para un look más limpio.
*   **Cursor:** Barra parpadeante.

---

## 🛠️ 5. Solución de Problemas (Troubleshooting)

*   **Si un atajo no funciona:** Verifica que no estés usando `AltGr` en lugar de `Alt`, o que el software de tu teclado (como Logitech Options) no esté interceptando la combinación.
*   **Si la fuente no carga:** Asegúrate de haber instalado la fuente `JetBrainsMono Nerd Font Mono` en Windows (haciendo clic derecho en el archivo `.ttf` -> "Instalar para todos los usuarios").
*   **Si la configuración no se aplica:** Abre el menú (`Ctrl + Shift + P`) y busca "Reload Configuration", o simplemente cierra y vuelve a abrir WezTerm.