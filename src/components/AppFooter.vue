<template>
  <v-footer color="grey-darken-4" class="text-white py-2" app>
    <v-container>
      <v-row justify="space-between" align="center">
        
        <v-col cols="12" md="4" class="text-center text-md-left mb-1 mb-md-0 text-body-2">
          <strong>Kevin Yassir Felix Sanchez</strong> • 1196791
        </v-col>
        
        <v-col cols="12" md="4" class="text-center mb-1 mb-md-0 text-caption text-grey-lighten-1">
          © {{ currentYear }} - kevin.felix59@uabc.edu.mx
        </v-col>

        <v-col cols="12" md="4" class="text-center text-md-right text-caption text-grey-lighten-1">
          Fecha actual: {{ currentDate }}
        </v-col>

      </v-row>
    </v-container>
  </v-footer>
</template>

<script setup>
import { ref, computed } from 'vue';

// Se obtiene la fecha actual usando el objeto Date() de JS y la propiedad computed
// de Vue para indicar que se debe actualizar
const date = new Date();
const currentDate = ref(date.toLocaleDateString('es-MX'));
const currentYear = computed(() => date.getFullYear());
</script>