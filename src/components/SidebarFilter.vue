<script lang="ts">
import { defineComponent } from 'vue';
import { Product } from '../App.vue';

export default defineComponent({
  name: 'SidebarFilter',
  methods: {
    applyFilter() {
      this.$emit('filter', (value: Product) => value.category === 'Audio');
    },
  },
});
</script>

<template>
  <!-- Aquí tu código de la barra de filtro -->
  <button @click="applyFilter">Aplicar Filtro</button>
</template>

<style scoped></style>
