<script>
import AppHeader from "./components/AppHeader.vue";
import ProductList from "./components/ProductList.vue";
import CardWrapper from "./components/CardWrapper.vue";

export default {
  components: {
    AppHeader,
    ProductList,
    CardWrapper
  },
  data() {
    return {
      products: []
    };
  },
  mounted() {
    this.products = [
      { id: 1, name: "Laptop", price: 50000 },
      { id: 2, name: "Mobile", price: 20000 },
      { id: 3, name: "Headphones", price: 3000 }
    ];
  },
  methods: {
    removeProduct(id) {
      this.products = this.products.filter(p => p.id !== id);
    }
  }
};
</script>

<template>
  <AppHeader title="Product Dashboard" />

  <CardWrapper>
    <p>Total Products: {{ products.length }}</p>
  </CardWrapper>

  <ProductList
    :products="products"
    @delete="removeProduct"
  />
</template>
