<script>
import Product from "./Product.vue";
import {eventBus} from "../main.js";

export default {
  name: "Products",
  data(){
    return {
      productList : [],
    }
  },
  components: {
    Product
  },
  created() {
    eventBus.$on("addProduct", (product) => {
      this.productList.push(product);
    });
  }

}
</script>

<template>
  <div class="row product-container">
    <Product v-for="product in productList">
      <img class="card-img-top" :src="product.selectedImage==null?'/src/assets/default.png':product.selectedImage" alt="Card image cap">
      <div class="card-body">
        <h5 class="card-title">{{ product.title }}</h5>
        <small>
          <strong>Adet : </strong> {{ product.count }}
        </small>
        <br>
        <small>
          <strong>Fiyat : </strong> {{ product.price }}
        </small>
        <br>
        <small>
          <strong>Tutar : </strong> {{ product.totalPrice }}
        </small>
      </div>
    </Product>
  </div>
</template>

<style>

</style>
