<template>
  <div>
    <h2>测试文本222</h2>
    <p>姓名：{{info.data.name}}</p>
    <p>年纪：{{info.data.age}}</p>
    <p>爱好：{{info.data.hobby}}</p>
    <div v-for="(item, index) in info.data.item" :key="index">
      <p>{{item.dd}}</p>
      <img :src="item.image" alt />
    </div>
  </div>
</template>



<script>
import axios from "axios";
export default {
  data() {
    return {};
  },
  //   asyncData() {
  //     return axios
  //       .get("http://rap2.taobao.org:38080/app/mock/242751/movielistinfo")
  //       .then(res => {
  //         return { info: res.data };
  //       });
  //   },
  async asyncData() {
    let { data } = await axios.get(
      "http://rap2.taobao.org:38080/app/mock/242751/movielistinfo"
    );
    return { info: data };
  }
};
</script>