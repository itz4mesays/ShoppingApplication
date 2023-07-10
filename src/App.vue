<template>
  <div id="app">
    
    <img alt="Vue logo" src="./assets/logo.png">

    <div class="container-fluid">

      <div class="row">
        <div class="col-md-3">
          <button type="button" class="btn btn-success position-relative">
          Total Item(s) in your cart
          <span class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger">
            {{ cart.length }}
            <span class="visually-hidden">Total Items</span>
          </span>
        </button>
        </div>
      </div>

      <div class="row">
        
        <div class="col-md-9">
           <div class="row">

              <div class="col-md-4" v-for="item in products" :key="item.id">
                  <product :product="item" v-on:add-to-cart="AddToCart(item)" :isItemInCart="isItemInCart(item)"></product>
              </div>

           </div>
        </div>

        <div class="col-md-3 my-5">
          <cart :items="cart" v-on:pay="payNow()" v-on:delete-from-cart="deleteFromCart($event)"></cart>
        </div>

      </div>
    </div>

    

  </div>
</template>

<script>

import Product from "@/components/ProductList.vue";
import Cart from "@/components/CartList.vue"
import products from "@/products.json";

export default {
  name: 'App',
  components: {
    Product,
    Cart
  },
  data() {
    return {
      products,
      cart: []
    }
  },
  methods: {
    AddToCart(item) {
      this.cart.push(item)
    },
    isItemInCart(product) {
      const item = this.cart.find(item => item.id === product.id)

      if(item) {
        return true
      }

      return false;
    },
    deleteFromCart(product) {
      this.cart = this.cart.filter(item => item.id !== product.id)
    },
    payNow() {
      this.cart = []

      alert('Shopping completed')
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
