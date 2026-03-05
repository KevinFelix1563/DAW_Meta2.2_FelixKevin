<template>
  <v-footer color="grey-darken-4" class="text-white py-4" app>
    <v-container>
      <v-row justify="center">
        <v-col cols="12" sm="8" md="6" class="text-center">
          <p class="mb-1 font-weight-bold">Kevin Yassir Felix Sanchez</p>
          <p class="mb-1">Matrícula: 1196791</p>
          <p class="mb-1">Fecha actual: {{ currentDate }}</p>
          <p class="text-caption mt-2 text-grey-lighten-1">
            © {{ currentYear }} - kevin.felix59@uabc.edu.mx
          </p>
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