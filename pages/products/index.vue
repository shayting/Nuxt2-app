<script>
export default {
  async asyncData({$axios}) {
    const res = await $axios.get("https://fakestoreapi.com/products");
    return { products: res.data };
  },
  methods: {
    seeDetail(id) {
      this.$router.push(`/products/${id}`);
    },
    openNewTab(id) {
      const routeData = this.$router.resolve({ path: `/products/${id}` });
      window.open(routeData.href, "_blank");
    },
  }
};
</script>
<template>
  <div class="container">
    <h1>all products</h1>
    <div class="cards-wrap">
      <div v-for="item in products" :key="item.id" class="card">
        <img :src="item.image" alt="" />
        <h6 class="name">{{ item.title }}</h6>
        <button
          @click.left="seeDetail(item.id)"
          @click.middle="openNewTab(item.id)"
        >
          see detail
        </button>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.cards-wrap {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
.card {
  border-radius: 10px;
  border: 1px solid #000;
  width: 200px;
  height: 360px;
  padding: 10px;
  img {
    width: 100%;
    height: 180px;
    object-fit: cover;
  }
  button {
    color: black;
    width: 100%;
    padding: 10px;
  }
}
</style>
