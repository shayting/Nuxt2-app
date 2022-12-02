<script>
import axios from "axios";
export default {
  async asyncData(context) {
    console.log(context.params.id);
    let isError = false;
    try {
      const res = await axios.get(
        `https://fakestoreapi.com/products/${context.params.id}`
      );
      return { product: res.data };
    } catch (err) {
      isError = true;
      console.log(err);
      return {
        isError,
      };
    }
  },
};
</script>

<template>
  <div class="wrap">
    <div class="container">
      <div>product-id:{{ product.id }}</div>
      <div class="img-wrap">
        <img :src="product.image" alt="" />
      </div>
      <h1>{{ product.title }}</h1>
    </div>
    <!-- <div v-if="isError" class="container">cannot find the product...</div> -->
  </div>
</template>

<style lang="scss" scoped>
.img-wrap {
  width: 300px;
  height: 300px;
  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>
