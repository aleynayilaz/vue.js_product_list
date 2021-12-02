<template>
  <div class="container">
    <!-- <myComp /> -->
    <div class="cart">
      <h3>Basket</h3>
      <ul>
        <li v-for="item in cartItems" :key="item.id">{{ item.title }}</li>
      </ul>
      <p v-if="cartItems.length == 0">Your basket is empty...</p>
    </div>
    <Product
      @addToBasket="cartItems.push($event)"
      :product="product"
      v-for="product in productList"
      :key="product.id"
    ></Product>
  </div>
</template>

<script>
import MainContainer from "./components/MainContainer.vue";
import Product from "./components/Product.vue";
export default {
  components: {
    myComp: MainContainer,
    Product,
  },
  data() {
    return {
      productList: [
        {
          id: 1,
          title: "Mackbook Pro",
          price: 100,
          count: 0,
          description: "Explain 1",
        },
        {
          id: 2,
          title: "Iphone",
          price: 50,
          count: 100,
          description: "Explain 2",
        },
        {
          id: 3,
          title: "Keyboard",
          price: 10,
          count: 1000,
          description: "Explain 3",
        },
      ],
      cartItems: [],
    };
  },
};
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.cart {
  margin-bottom: 50px;
}
</style>
