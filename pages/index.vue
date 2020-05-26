<template>
  <!-- <section class="container"> -->
  <div>
    <ul>
      <li>
        <!-- <a href="/">HOME</a> -->
        <nuxt-link :to="{name:'index'}">HOME</nuxt-link>
      </li>
      <li>
        <!-- <a href="/about">ABOUT</a> -->
        <nuxt-link :to="{name:'About-About'}">ABOUT</nuxt-link>
      </li>
      <li>
        <!-- <a href="/news">NEWS</a> -->
        <nuxt-link :to="{name:'News-News',params:{newsId:52066}}">NEWS</nuxt-link>
      </li>
    </ul>
    <div style="height:300px;width:300px;">
      <img src="~static/pic1.jpg" alt="">
    </div>
  </div>
  <!-- </section> -->
</template>

<script>
import AppLogo from "~/components/AppLogo.vue";

export default {
  components: {
    AppLogo
  }
};
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

