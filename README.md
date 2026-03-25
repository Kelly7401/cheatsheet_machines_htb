# ⚡ HTB Machines CheatSheet

¡Bienvenido al **HTB Machines CheatSheet** de d1se0!  

Esta página web está diseñada para **visualizar de manera rápida y visual todas las máquinas hackeadas en Hack The Box (HTB)** por el usuario [d1se0](https://app.hackthebox.com/users/1940973) (HTB ID: 1940973). La idea es tener un dashboard interactivo que permita consultar técnicas usadas, dificultad, fechas y otros detalles de cada máquina.

---

## 🔹 Funcionalidades

1. **Listado de máquinas**  
   La tabla muestra todas las máquinas que has completado en HTB, incluyendo información como:
   - Nombre de la máquina (en **negrita**)
   - Dificultad (Easy, Intermediate, Hard, Insane) con **badges de colores**
   - Estado (Activa / Inactiva)
   - Hecha / No hecha
   - OS (Windows o Linux) representado con badges
   - URL de la máquina o writeup
   - Técnicas empleadas en cada máquina (badges visuales con efecto blur y colores mates)
   - Fecha de resolución

2. **Badges visuales para técnicas y dificultad**  
   - Técnicas como `sqli`, `xss`, `proxy`, `subdominios`, `python3`, etc. se muestran con badges de colores mates y **efecto difuminado (blur)** para mejor visualización.
   - Dificultad de cada máquina con badge codificado:
     - Easy → verde
     - Intermediate → amarillo
     - Hard → rojo
     - Insane → morado

3. **Tabla interactiva con DataTables**
   - **Búsqueda rápida**  
   - **Paginación**  
   - Visualización agradable con colores oscuros y estilo moderno
   - **Sin orden automático**: la tabla respeta el orden original del Excel (`htb_machines_UPDATE.xlsx`), mostrando las máquinas en el mismo orden que las registraste.

4. **Soporte para Excel**
   - La página carga automáticamente los datos desde un archivo Excel (`.xlsx`) mediante `SheetJS`.
   - Cualquier actualización en el archivo Excel se refleja directamente al recargar la página.

---

## 🔹 Cómo funciona

1. **Estructura del proyecto**

```
/htb-dashboard/
├─ index.html # Página principal con la tabla
├─ htb_machines_UPDATE.xlsx # Excel con los datos de máquinas
├─ README.md # Este archivo
└─ HackNerdFont-Regular.ttf # Fuente personalizada
```


2. **Tecnologías utilizadas**
- [Bootstrap 5](https://getbootstrap.com/) → Diseño y estilos responsivos
- [DataTables](https://datatables.net/) → Tabla interactiva con búsqueda y paginación
- [SheetJS / XLSX](https://sheetjs.com/) → Carga de Excel en el navegador
- CSS moderno → Colores oscuros, badges mates, efectos blur
- Fuente personalizada: `Hack Nerd Font` para un look de terminal

3. **Carga de datos**
- La página obtiene los datos del archivo `htb_machines_UPDATE.xlsx`
- Cada fila representa una máquina completada en HTB
- La función `createTable()` convierte los datos del Excel a HTML, aplicando **badges y estilos personalizados**

4. **Orden de la tabla**
- Para mantener la **misma secuencia que en Excel**, la tabla **no realiza orden automático**
- Si se desea invertir la visualización (mostrar lo último primero), el array de JSON se puede invertir con `json.reverse()`

5. **Técnicas como badges**
- La función `getTechBadge(tech)` genera un badge por cada técnica usada, aplicando:
  - Colores mates y distintos por técnica
  - Difuminado con `backdrop-filter: blur(8px)`
  - Texto blanco con sombra para legibilidad

---

## 🔹 Personalización

- Para **añadir nuevas técnicas**, solo se necesita:
1. Crear una clase CSS `.badge-nombre` con color mate y difuminado.
2. Asegurarse que la función `getTechBadge(tech)` normaliza el nombre correctamente (`toLowerCase().replace(/\s+/g, '-')`).

- La dificultad y OS se representan automáticamente con badges:
- Windows → azul
- Linux → naranja
- Dificultades → verde/amarillo/rojo/morado

---

## 🔹 Uso

1. Clonar el repositorio:

```bash
git clone https://github.com/D1se0/cheatsheet_machines_htb.git
```
2. Abrir `index.html` en un navegador moderno
3. Actualizar el archivo `htb_machines_UPDATE.xlsx` según vayas completando nuevas máquinas

---

## 🔹 Créditos

- Página creada y mantenida por `d1se0` (HTB ID: `1940973`)
- Inspiración y estilos basados en dashboards modernos de Hack The Box y DataTables

---

## 🔹 Licencia

Este repositorio es de uso personal. Puedes visualizar, modificar y mejorar el dashboard para tu propio seguimiento de HTB.
No redistribuir sin permiso del autor.
