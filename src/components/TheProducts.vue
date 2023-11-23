<template>
  <ul>
    <li v-for="product in products" :key="product.id">
      {{ product.name }} - {{ product.category }}
    </li>
  </ul>
</template>

<script lang="ts">
export default {
  name: 'TheProducts',
  props: ['products'],
};
</script>
