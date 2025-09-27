<script setup>

import {ref, reactive} from 'vue'

//HEADER
const title = 'Mini Dashboard Vue'
const saludo = 'Hola'
const nombre = ref('Pipe')
const contador = ref(0)
const activo = ref(true)

//FRUTAS
const frutas = ref(['Manzana', 'Pera', 'Naranja', 'Frutilla', 'Kiwi'])
const nuevaFruta = ref('')

//FUNCION PARA AGREGAR FRUTA
const agrgarFruta = () => {
  const f = nuevaFruta.value.trim()
  if (!f) return
  frutas.value.push(f)
  nuevaFruta.value = ''
}

//PERSONAS
const personas = ref([
  { id: 1, nombre: 'Ana', edad: 23, email: 'ana@ejemplo.com', ciudad: 'Rosario'},
  { id: 2, nombre: 'Luis', edad: 17, email: 'luis@ejemplo.com', ciudad: 'Córdoba'},
  { id: 3, nombre: 'María', edad: 30, email: 'maria@ejemplo.com', ciudad: 'Buenos Aires'}
])

//ARRAY PARA CONTROLAR QUE PERSONAS MUESTRAN DETALLES
const detalles = ref([])

//FUNCION PARA MOSTRAR/OCULTAR DETALLES
const toggleDetalles = (id) => {
  if(detalles.value.includes(id)) {
    detalles.value = detalles.value.filter(i => i !== id)
} else {
  detalles.value.push(id)
}
}

//USUARIO (objeto simple)
const usuario = reactive({
  username: 'pipe89', 
  role: 'estudiante', 
  active: true})

//MENSAJES
const nuevoMensaje = ref('')
const mensajes = ref([])

const enviarMensaje = () => {
  const texto = nuevoMensaje.value.trim()
  if (!texto) return
  mensajes.value.push(texto)
  nuevoMensaje.value = ''
}

//EVENTOS ESPECIALES
const sumar = () => contador.value++
const restar = () => contador.value--
const onRightClick = (e) => {
  e.preventDefault()
  alert('Click derecho detectado (.right + .prevent)')
}
const onMiddleClick = () => alert('Click con boton medio')
const onceAction = () => alert('Este evento solo se dispara una vez (.once)')
const parentClick = () => console.log('Click en el padre')
const childClick = () => alert('Click en boton hijo (detenido con .stop)')




const clickPadre = () => console.log('Click en PADRE')
const clickHijoSinStop = () => console.log('Click en HIJO SIN .stop')
const clickHijoConStop = () => console.log('Click en HIJO CON .stop')

</script>

<template>
  <div class="app">
    <!--HEADER-->
    <header>
      <h1>{{ title }}</h1>
      <p>{{saludo}}, {{ nombre }}, - Contador: {{ contador }}</p>
      <button @click="sumar">+</button>
      <button @click="restar">-</button>
    </header>

    <!--FRUTAS (V-FOR ARRAY SIMPLE)-->
    <section class="card">
      <h2>Frutas</h2>
      <ul v-for="(fruta, idx) in frutas" :key="idx">
          {{ idx + 1 }} - {{ fruta }}
      </ul>
      <input v-model="nuevaFruta" placeholder="Agregar fruta"/>
      <button @Click="agregarFruta">Agregar</button>
    </section>

    <!--PERSONAS (V-FOR ARRAY DE OBJETOS)-->
    <section class="card">
      <h2>Personas</h2>
      <ul v-for="persona in personas" :key="persona.id">
          <strong>{{ persona.nombre }}</strong> - {{ persona.edad }} años
          <button @click="toggleDetalles(persona.id)">
            {{ detalles.includes(persona.id) ? 'Ocultar' : 'Mostrar' }} detalles
          </button>

          <!--Detalles solo si esta activo en detalles-->
          <div v-if="detalles.includes(persona.id)">
            <p>Email: {{ persona.email }}</p>
            <p>Ciudad: {{ persona.ciudad }}</p>
          </div>
      </ul>
    </section>

    <!--USUARIO (V-FOR EN OBJETO)-->
    <section class="card">
      <h2>Usuario</h2>
      <ul v-for="(valor, clave) in usuario" :key="clave">
          {{clave}}: {{ valor }}
      </ul>
    </section>

    <!--MENSAJES-->
    <section class="card">
      <h2>Mensajes</h2>
      <input v-model="nuevoMensaje" @keyup.enter="enviarMensaje" placeholder="Escribe y presiona enter"/>
      <ul>
        <li v-for="(m, i) in mensajes" :key="i">{{ m }}</li>
      </ul>
    </section>

    <!--EVENTOS ESPECIALES-->
    <section class="card">
      <h2>Eventos especiales</h2>
      <button @click.right.prevent="onRightClick"> Click derecho</button>
      <button @click.middle="onMiddleClick"> Click medio</button>
      <button @click.once="onceAction">Una vez</button>
    </section>

    <div @click="parentClick" class="caja">
      <button @click.stop="childClick">Hijo con .stop</button>
    </div>



    <!-- EJEMPLO PROPAGACIÓN -->
<section class="card">
  <h2>Propagación de Eventos</h2>
  <div 
    @click="clickPadre" 
    style="border: 2px solid #333; padding: 20px; margin-bottom: 10px;"
  >
    Soy el PADRE
    <button @click="clickHijoSinStop">Hijo SIN .stop</button>
    <button @click.stop="clickHijoConStop">Hijo CON .stop</button>
  </div>
</section>




    <!--CLASES DINAMICAS-->
    <section class="card">
      <h2>Clases dinamicas</h2>
      <p v-if="activo">Activo</p>
      <p v-else>Inactivo</p>
      <p :class="{amarillo: activo, resaltado: contador > 0}">Este texto cambia de estilo segun las condiciones</p>
      <button @click="activo = !activo">Boton activar</button>
    </section>
  </div>
</template>

<style scoped>
.app {
  max-width: 800px;
  margin: auto;
  font-family: sans-serif;
}
header {
  text-align: center;
  margin-bottom: 20px;
}
.card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 15px;
  margin-bottom: 20px;
}
.preview {
  max-width: 100%;
  border-radius: 8px;
}
ul {
  padding-left: 20px;
}
button {
  margin: 5px;
  padding: 5px 10px;
}
.amarillo {
  color: goldenrod;
}
.resaltado {
  font-weight: bold;
  background-color: #f0f0f0;
}
.caja {
  border: 1px dashed #aaa;
  padding: 10px;
  margin-top: 10px;
}
</style>