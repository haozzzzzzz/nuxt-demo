|-- .nuxt                            // Nuxt自动生成，临时的用于编辑的文件，build
|-- assets                           // 用于组织未编译的静态资源入LESS、SASS 或 JavaScript
|-- components                       // 用于自己编写的Vue组件，比如滚动组件，日历组件，分页组件
|-- layouts                          // 布局目录，用于组织应用的布局组件，不可更改。
|-- middleware                       // 用于存放中间件
|-- pages                            // 用于存放写的页面，我们主要的工作区域
|-- plugins                          // 用于存放JavaScript插件的地方
|-- static                           // 用于存放静态资源文件，比如图片
|-- store                            // 用于组织应用的Vuex 状态管理。
|-- .editorconfig                    // 开发工具格式配置
|-- .eslintrc.js                     // ESLint的配置文件，用于检查代码格式
|-- .gitignore                       // 配置git不上传的文件
|-- nuxt.config.json                 // 用于组织Nuxt.js应用的个性化配置，已覆盖默认配置
|-- package-lock.json                // npm自动生成，用于帮助package的统一性设置的，yarn也有相同的操作
|-- package-lock.json                // npm自动生成，用于帮助package的统一性设置的，yarn也有相同的操作
|-- package.json                     // npm包管理配置文件


1. 修改域名，端口  
    1. 在package.json里面配置   
        "config"{
            "nuxt"："127.0.0.1",
            "port":8080
        }
    2. 全局配置css
2. 路由配置，参数传递
    1. 使用<nuxt-link :to="{name:'路由名'}">
    2. <nuxt-link :to="{name:'路由名'， params：{newsId：5555666 }}"> 使用params传参
    3. 使用 {{$route.params.newsId}} 接收
3. 动态路由，参数校验
```
    1. 路由用<nuxt-link :to="{name:'news-id',params:{id:123}}"><nuxt-link>
    用nuxt-link 包裹 to 路由name params传参
    2. 参数检验
    validate({ params }) {
        // 验证不通过就返回404页面
        return /^\d+$/.test(params.id);
    },
```
4. 默认模板，默认布局
```
    1. 默认模板:
        在根目录创建app.html
        <!DOCTYPE html> // 注释
        <html lang="en">
        <head>
           {{ HEAD }}
        </head>
        <body>
            <p>jspang.com 技术胖的博客</p>
            {{ APP }}
        </body>
        </html>
        // HEAD 读取的是nuxt.config.js里的信息
        // APP 读取的是pages文件夹下的主体页面 都需要大写 写完重新运行项目
    2. 默认布局:
        位置根目录下的layouts/default.vue 
        在<nuxt /> 上面加上统一布局即可
        <nuxt /> 是每个页面的内容
```
5. 错误页面,个性meta标签
```
    1. 错误页面 根目录下的layouts文件夹下建立一个error.vue文件
    <h2 v-if="error.statusCode==404">404页面不存在</h2>
    <h2 v-else>500服务器错误</h2>
    <ul>
        <li><nuxt-link to="/">HOME</nuxt-link></li>
    </ul>
     
    <script>
        export default {
          props:['error'],
        }
    </script>
    2. 个性meta标签
        1.在data里使用this.$route.params.title 来接收传递过来的title
        <li><nuxt-link :to="{name:'news-id',params:{id:123,title:'jspang.com'}}">News-1</nuxt-link></li>
        data(){
            return{
              title:this.$route.params.title,
            }
         },
        2.用head方法来设置头部信息
        //独立设置head信息
          head(){
              return{
                title:this.title,
                meta:[
                 {hid:'description',name:'news',content:'This is news page'}
                ]// 建议利用 hid 键为meta标签配一个唯一的标识编号
              }
            }
        }
```
6. asyncData方法获取数据
```
    1. asyncData(){
        return axios.get('xxx').then((res)=>console.log（res）)
    }
    
    使用async await 简化操作，解决异步,
    async asyncData(){
        const {data} =await axios.get('xxx')
        return {info:data}
    }
```
7.  静态资源打包
```
    1. 直接用~引入图片  
    例如： <div><img src="~static/logo.png" /></div>
    2. 打包
    npm run generate 
    在dist文件夹下 换成自己设置的端口域名即可 右键打开live-server
```