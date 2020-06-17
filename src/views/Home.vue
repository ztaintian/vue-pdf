<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  // components: {
  //   HelloWorld
  // },
  mounted() {
    let url =
      "https://apis.map.qq.com/ws/location/v1/ip?ip=61.135.17.68&key=SSGBZ-YXYWO-FQJW7-SXTBH-GMKAH-2MBTN&output=jsonp";
    this.$jsonp(url, {})
      .then(json => {
        console.log(json); //附近街道地址信息
      })
      .catch(err => {
        console.log(err);
      });
  }
};
</script>
