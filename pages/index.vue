<template>
  <div class="container">
    <h1>home</h1>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  // asyncData(context){
  //   context.$DemoTest.log('asyncData 階段注入')
  //   console.log(context.$axios)
  // },
  // --- 解構方法 ---
  asyncData({ $axios, $DemoTest }) {
    $DemoTest.log("asyncData 階段注入");
    console.log($axios);
  },
  mounted() {
    this.$DemoTest.log("plugins 注入測試");
    console.log(this);
  },
};
</script>
