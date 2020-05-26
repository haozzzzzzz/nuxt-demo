<template>
  <div>
    <p>News-Content [{{$route.params.id}}]</p>
    <a href="/">Home</a>
  </div>
</template>
<script>
export default {
  validate({ params }) {
    return /^\d+$/.test(params.id);
  },
  data() {
    return {
      title: this.$route.params.title
    };
  },
  head() {
    return {
      title: this.title,
      // 个性meta标签设置，利于seo优化
      meta: [{ hid: "description", name: "news", content: "This is news page" }]
    };
  }
};
</script>