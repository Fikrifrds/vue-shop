<template>
  <div class="row">
    <div
      class="card"
      style="width: 15rem;"
      v-for="item in products"
      :key="item.id"
    >
      <img :src="item.imgUrl" class="card-img-top" :alt="item.title" />
      <div class="card-body">
        <p class="card-title">{{ item.title }}</p>
        <p class="card-text">$ {{ item.price.toLocaleString() }}</p>
        <button class="btn btn-primary" @click="addToCart(item); scrollToTop()">
          Add to cart
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState, mapMutations } from "vuex";

export default {
  name: "Shop",
  mounted() {
    this.getProductData();
  },
  computed: {
    ...mapState(["products"]),
  },
  methods: {
    ...mapMutations(["addToCart", "getProductData"]),
    scrollToTop() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth'
      })
    }
  },
};
</script>

<style scoped>
.card {
  padding: 20px;
  border: none;
}
</style>
