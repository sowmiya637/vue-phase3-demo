<script>
export default {
  props: {
    products: Array
  },
  emits: ["delete"],
  methods: {
    deleteProduct(id) {
      this.$emit("delete", id);
    }
  }
};
</script>

<template>
  <ul>
    <li v-for="p in products" :key="p.id">
      {{ p.name }} - ₹{{ p.price }}
      <button @click="deleteProduct(p.id)">Delete</button>
    </li>
  </ul>
</template>

<style scoped>
button {
  margin-left: 10px;
}
</style>
