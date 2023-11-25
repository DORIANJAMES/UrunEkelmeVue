<script>
import Product from "./Product.vue";
import {eventBus} from "../main.js";

export default {
  name: "Products",
  data() {
    return {
      productList: [],
    }
  },
  components: {
    Product
  },
  created() {
    eventBus.$on("addProduct", (product) => {
      if (this.productList.length < 10) {
        this.productList.push(product);
        eventBus.$emit("productListLength", this.productList.length)
      } else {
        alert("Sadece 10 ürün eklenebilir");
      }
    });
  }
}
</script>

<template>
  <div class="row product-container">
    <Product v-for="product in productList">
      <img class="card-img-top" :src="product.selectedImage==null?'/src/assets/default.png':product.selectedImage"
           alt="Card image cap">
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
