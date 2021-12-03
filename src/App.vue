<template>
  <div class="container">
    <!-- <myComp /> -->
    <div class="cart">
      <h3>Basket</h3>
      <ul>
        <li v-for="item in cartItems" :key="item.id">
          {{ item.title }} - {{ item.count }}
        </li>
      </ul>
      <p v-if="cartItems.length == 0">Your basket is empty...</p>
    </div>
    <Product
      @addToBasket="addToCard(product)"
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
          count: 1,
          description: "Explain 1",
        },
        {
          id: 2,
          title: "Iphone",
          price: 50,
          count: 1,
          description: "Explain 2",
        },
        {
          id: 3,
          title: "Keyboard",
          price: 10,
          count: 1,
          description: "Explain 3",
        },
      ],
      cartItems: [],
    };
  },
  methods: {
    addToCard(product) {
      let indx = this.cartItems.findIndex((item) => item.id === product.id);
      if (indx === -1) {
        this.cartItems.push(product);
      } else {
        this.cartItems[indx].count++;
      }
    },
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
