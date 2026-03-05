<template>
  <v-app>
    <!-- Componente de encabezado-->
    <AppHeader />
    
    <v-main class="bg-grey-lighten-4">
      <v-container class="py-8">
        
        <!-- v-alert para mostrar alertas si no se puede consumir la API de Picsum-->
        <!-- Solo se muestra si la variable reactiva "error" tiene algun valor utilizando v-if -->
        <v-alert
          v-if="error"
          type="error"
          title="Error de conexión"
          text="Hubo un problema al obtener las imágenes de Picsum. Por favor, intenta nuevamente."
          class="mb-6"
          closable
          @click:close="error = null"
        ></v-alert>

        <!-- Tarjetas contenidas en un v-row -->
        <v-row justify="center">
          <v-col cols="12" md="6">
            <TarjetaConImagen
              :urlImagen="imagenes[0].url"
              titulo="Fotografía Aleatoria 1"
              descripcion="Esta es una imagen generada dinámicamente consumiendo la API de Picsum Photos a través de una petición fetch."
              :autor="imagenes[0].autor"
            />
          </v-col>

          <v-col cols="12" md="6">
            <TarjetaConImagen 
              :urlImagen="imagenes[1].url"
              titulo="Fotografía Aleatoria 2"
              descripcion="Esta es una imagen generada dinámicamente consumiendo la API de Picsum Photos a través de una petición fetch."
              :autor="imagenes[1].autor"
            />
          </v-col>

        </v-row>

        <v-row justify="center" class="my-6">
          <v-col cols="auto">
            <v-btn
              color="primary"
              size="large"
              prepend-icon="mdi-refresh"
              :loading="cargando"
              :disabled="cargando"
              @click="actualizarImagenes"
            >
              Actualizar Imágenes
            </v-btn>
          </v-col>
        </v-row>

        <v-row justify="center">
          <v-col cols="12">
             </v-col>
        </v-row>

      </v-container>
    </v-main>
    <!-- Componente de footer-->
    <AppFooter />
  </v-app>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'
import TarjetaConImagen from './components/TarjetaConImagen.vue'

// Estado reactivo
const imagenes = ref([
  { url: '', autor: '' },
  { url: '', autor: '' }
])
const cargando = ref(false) // Estado de carga
const error = ref(null) // Posibles errores

// Función asincrona para obtener y actualizar imagenes
const actualizarImagenes = async () => {
  cargando.value = true // Se activa el estado de cargando
  error.value = null
  
  try {
    // Petición a Picsum
    const response = await fetch('https://picsum.photos/v2/list?page=1&limit=50')
    
    if (!response.ok) {
      throw new Error('Error en la respuesta de la API de red') // Se capturan errores
    }
    
    const data = await response.json() // Procesar respuesta JSON
    
    // Se selecciona dos indices aleatorios
    let index1 = Math.floor(Math.random() * data.length)
    let index2
    do { //Mediante un ciclo do-while se verifica asigna indice a index2 hasta que sea diferente al 1
      index2 = Math.floor(Math.random() * data.length)
    } while (index1 === index2) 
    
    // Se actualiza imagenes usando el JSON que se nos entrego.
    imagenes.value = [
      {
        url: `https://picsum.photos/id/${data[index1].id}/500/300`, 
        autor: data[index1].author
      },
      {
        url: `https://picsum.photos/id/${data[index2].id}/500/300`,
        autor: data[index2].author
      }
    ]
    
  } catch (err) {
    console.error(err) // Si sucede un error se muestra en consola
    error.value = err.message 
  } finally {
    cargando.value = false // Si todo se realizo se desactiva el estado de cargando
  }
}

// Se cargan las imagenes al montar las tarjetas al DOM 
onMounted(() => {
  actualizarImagenes()
})
</script>