<template>
  <v-app>
    <AppHeader />
    
    <v-main class="bg-grey-lighten-4">
      <v-container class="fill-height">
        <v-row justify="center" align="center">
          <v-col class="text-center">
            <h1 class="text-h4 text-grey-darken-1">
              Faltan tarjetas y tablas.
            </h1>
          </v-col>
        </v-row>
      </v-container>
    </v-main>

    <AppFooter />
  </v-app>
</template>

<script setup>
// Se importan los componentes
import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'
</script>

<style scoped>

</style>