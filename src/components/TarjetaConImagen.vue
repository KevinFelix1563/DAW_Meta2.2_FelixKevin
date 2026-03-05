<template>
  <v-card class="mx-auto h-100 d-flex flex-column" max-width="500" elevation="4">
    
    <!-- Componente de Vuetify para mostrar la imagen -->
    <v-img
      :src="urlImagen"
      height="250"
      cover
    >
      <!-- Slot que se muestra mientras la imagen está cargando -->
      <template v-slot:placeholder>
        <div class="d-flex align-center justify-center fill-height bg-grey-lighten-2">
          <!-- Indicador de circulo de carga -->
          <v-progress-circular color="primary" indeterminate></v-progress-circular>
        </div>
      </template>
    </v-img>

    <v-card-title class="text-h6 font-weight-bold mt-2">
      {{ titulo }}
    </v-card-title>

    <v-card-subtitle class="text-subtitle-1 text-primary-darken-1 font-weight-medium pb-2">
      Fotografía por: {{ autor }}
    </v-card-subtitle>

    <!-- flex-grow-1 permite que este elemento ocupe el espacio disponible -->
    <v-card-text class="text-body-2 text-grey-darken-2 flex-grow-1">
      {{ descripcion }}
    </v-card-text>
    
  </v-card>
</template>

<script setup>

// Definición de las props que el componente recibira desde App
defineProps({

  urlImagen: {
    type: String,
    required: true
  },

  titulo: {
    type: String,
    required: true
  },

  descripcion: {
    type: String,
    required: true
  },

  autor: {
    type: String,
    required: true
  }

})
</script>