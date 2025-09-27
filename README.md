# Mini Dashboard Vue 3 – Ejemplos interactivos

Este proyecto es un **mini dashboard educativo en Vue 3** que sirve para aprender y practicar conceptos clave de Vue, como reactividad, directivas, eventos y clases dinámicas.

---

## Propósito y aprendizaje por sección

### Header + Contador

- Propósito: Mostrar datos e interactuar con botones
- Qué se practica: ref, interpolación {{ }}, eventos @click

### Frutas

- Propósito: Gestionar una lista de elementos
- Qué se practica: v-for con array simple, v-model, función para agregar elementos

### Personas

- Propósito: Listar objetos y mostrar detalles dinámicos
- Qué se practica: v-for con array de objetos, v-if dentro de v-for, control de estado con array de ids

### Usuario

- Propósito: Iterar sobre un objeto simple
- Qué se practica: v-for sobre objeto, reactive, claves y valores dinámicos

### Mensajes

- Propósito: Input reactivo y lista dinámica
- Qué se practica: v-model, eventos de teclado @keyup.enter, v-for para renderizar mensajes

### Eventos especiales

- Propósito: Practicar modificadores de eventos
- Qué se practica: .right, .middle, .once, .stop, propagación de eventos

### Propagación Padre-Hijo

- Propósito: Entender event bubbling
- Qué se practica: Diferencia entre click en hijo con .stop y sin .stop

### Clases dinámicas

- Propósito: Cambiar estilos según condiciones
- Qué se practica: :class con objeto, reactividad, combinar condiciones

---

## Sugerencia de uso

1. Recorrer la app sección por sección y probar los botones, inputs y eventos.  
2. Modificar valores y funciones para ver cómo cambia la vista en tiempo real.  
3. Agregar comentarios en el código explicando qué hace cada parte.  
4. Experimentar con nuevas propiedades: por ejemplo, cambiar colores, agregar nuevas frutas o personas.  

---

## Recursos oficiales

- [Vue 3 Script Setup](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup)  
- [IDE Support for Vue](https://vuejs.org/guide/scaling-up/tooling.html#ide-support)  

---

## Tecnologías utilizadas

- Vue 3  
- Vite  
- HTML / CSS / JavaScript  

---

## Instalación y ejecución

```bash
# Clonar repositorio
git clone <URL_DEL_REPOSITORIO>

# Entrar en la carpeta del proyecto
cd nombre-del-proyecto

# Instalar dependencias
npm install

# Ejecutar el proyecto
npm run dev
