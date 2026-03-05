<template>
  <v-card class="mt-4 mb-8" elevation="3">
    <!-- mt-4 y mb-8 agregan margen superior e inferior -->
    <v-card-title class="bg-primary text-white text-h6 py-3">
      Perfil Técnico y Habilidades
    </v-card-title>
    
    <v-table hover>
        <!-- hover permite resaltar la fila cuando el cursor pasa sobre ella -->
      <thead>
        <tr>
          <th class="text-left font-weight-bold text-subtitle-1">Tecnología / Herramienta</th>
          <th class="text-left font-weight-bold text-subtitle-1">Nivel de Dominio</th>
          <th class="text-left font-weight-bold text-subtitle-1">Contexto de Uso / Proyectos</th>
        </tr>
      </thead>
      <tbody>
        <!-- v-for recorre el arreglo "habilidades" -->
        <!-- Por cada elemento se crea una fila en la tabla -->
        <!-- :key ayuda a Vue a identificar cada elemento renderizado -->
        <tr v-for="item in habilidades" :key="item.tecnologia">
          <td class="font-weight-medium">{{ item.tecnologia }}</td>
          <td>
            <v-chip :color="item.color" size="small" class="font-weight-bold">
              {{ item.nivel }}
            </v-chip>
          </td>
          <td class="text-body-2 text-grey-darken-2">{{ item.contexto }}</td>
        </tr>
      </tbody>
    </v-table>
  </v-card>
</template>

<script setup>
import { ref } from 'vue'

const habilidades = ref([
  { 
    tecnologia: 'Java', 
    nivel: 'Intermedio', 
    contexto: 'Implementación de algoritmos de búsqueda y de ordenamiento.',
    color: 'yellow'
  },
  { 
    tecnologia: 'Python (TensorFlow & Scikit-learn)', 
    nivel: 'Principiante', 
    contexto: 'Entrenamiento de modelos de clasificación de baja escala con TensorFlow y keras',
    color: 'blue'
  },
  { 
    tecnologia: 'C', 
    nivel: 'Intermedio', 
    contexto: 'Desarrollo de interprete con comandos básicos como cat, cp y rm.',
    color: 'yellow'
  },
  { 
    tecnologia: 'Vue 3 & Bootstrap 5', 
    nivel: 'Principiante', 
    contexto: 'Diseño de layouts responsivos a tamaño de pantalla y uso de elementos reactivos.',
    color: 'blue'
  },
  { 
    tecnologia: 'Electrónica', 
    nivel: 'Avanzado', 
    contexto: 'Sistema de iluminación con sensores, pantalla de baja escala con LEDs y microcontrolador.',
    color: 'green'
  }
])
</script>