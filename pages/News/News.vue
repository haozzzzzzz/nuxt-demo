<template>
  <div>
      <h2>News Index page</h2>
      <p>路由接收ID：{{$route.params.newsId}}</p>
      <ul>
        <li><a href="/">Home</a></li>
        <li><nuxt-link :to="{name:'News-id',params:{id:aaa}}">new-1</nuxt-link></li>
        <li><nuxt-link :to="{name:'News-id',params:{id:456,title:'hello-howar'}}">new-2</nuxt-link></li>
      </ul>
  </div>
</template>