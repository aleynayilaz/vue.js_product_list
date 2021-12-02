<template>
  <div class="product">
    <strong>{{ product.title }}</strong>
    <p>{{ product.description }}</p>
    <strong>Price : {{ product.price }} | Number : {{ product.count }} </strong>
    <button @click="addToBasket(product)">Add to Basket</button>
  </div>
</template>

<script>
export default {
  props: ["product"],
  methods: {
    addToBasket(product) {
      this.$emit("addToBasket", product);
    },
  },
};
</script>

<style>
.product {
  border: 2px dashed #666;
  padding: 5px 10px;
  width: 300px;
  margin-bottom: 10px;
  margin: 5px;
}
.product:hover {
  border: 2px solid #666;
  transition: all 0.5;
}
</style>
