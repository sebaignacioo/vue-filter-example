<script lang="ts">
import SidebarFilter from './components/SidebarFilter.vue';
import SearchBar from './components/SearchBar.vue';
import TheProducts from './components/TheProducts.vue';

export type Product = {
  id: number;
  name: string;
  price: number;
  description: string;
  category: string;
};

export default {
  components: {
    SearchBar,
    SidebarFilter,
    TheProducts,
  },
  data() {
    return {
      allProducts: [] as Product[], // Aquí irían todos tus productos
      filteredProducts: [] as Product[],
    };
  },
  async mounted() {
    this.allProducts = (
      await fetch('/data.json').then((res) => res.json())
    ).data;
    this.filteredProducts = this.allProducts;
  },
  methods: {
    handleSearch(searchTerm: string) {
      this.filteredProducts = this.allProducts.filter((product) =>
        product.name.toLowerCase().includes(searchTerm.toLowerCase()),
      );
    },
    handleFilter(filterCriteria: (value: Product) => boolean) {
      this.filteredProducts = this.allProducts.filter((product) =>
        filterCriteria(product),
      );
    },
  },
};
</script>

<template>
  <div>
    <SearchBar @search="handleSearch" />
    <SidebarFilter @filter="handleFilter" />
    <TheProducts :products="filteredProducts" />
  </div>
</template>

<style scoped></style>
