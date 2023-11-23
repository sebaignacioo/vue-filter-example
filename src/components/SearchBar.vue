<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'SearchBar',
  methods: {
    onSearch(event: any) {
      const value = event.target.value;
      this.$emit('search', value);
    },
  },
});
</script>

<template>
  <div class="card">
    <p>Búsqueda</p>
    <input type="text" @change="onSearch" placeholder="Buscar" />
  </div>
</template>

<style scoped></style>
