## pages预渲染
1. static generation
    分为静态html和外部数据的渲染;    SSG
        外部数据:
            1. 外部数据获取 getStaticProps  
                revalidation: 40  ISR  增量静态生成
            2. 外部数据的Path getStaticPath   动态路由/数据依赖外部时必须使用;
2. server-side generation     SSR
    getServerSideProps

3. CSR
    使用useEffect/useSWR等在page里面;


## 预渲染的三个方法 
只能再Pages页面里面使用,不能再components组件里面用;

造成此限制的原因之一是 React 在渲染页面之前需要拥有所有必需的数据。


## nextjs使用/api/路由和getServerSideProps的区别

都是处理服务器端请求的机制，但它们的使用场景和作用不同

/api/路由可以提供GET,POST等请求方式,也可以给外部使用;

getServerSideProps: 是在预渲染页面时使用,用途为在页面渲染之前获取服务器端的数据，并将其直接传递给页面组件。


## APP routing 和 Page routing区别

https://segmentfault.com/a/1190000045123079

优先使用page routing


## Handbook

### Image
有以下属性:
    
    <Image src='/abc.jpg' alt='abc' width={400} height={400} placeholder="blur" [priority]/>

nextjs加载器, 使得远程图片 /abc.jpg可以运行

使用远程图片时候, 需要在next.config.js
```js
module.exports = {
  images: {
    domains: ['example.com', 'example2.com'],
  },
}
```

priority属性: 可以使nextjs优先加载这个图像, 最好是页面中最大的那个图片

layout="fill": 填充容器,不知道图片尺寸


### useRoute
报错为只能在客户端渲染页面使用,如何确定此页面是客户端还是服务端的呢?

onClick={() => router.push('/sg')}      right

onClick={router.push('/sg')}            wrong

router.push         浏览器可以返回;
router.replace      浏览器不能返回;

