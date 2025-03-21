## pages 预渲染

1. static generation
       分为静态 html 和外部数据的渲染; SSG
       外部数据: 1. 外部数据获取 getStaticProps  
       revalidation: 40 ISR 增量静态生成 2. 外部数据的 Path getStaticPath 动态路由/数据依赖外部时必须使用;

2. server-side generation SSR
      getServerSideProps

3. CSR
       使用 useEffect/useSWR 等在 page 里面;

## 预渲染的三个方法

只能再 Pages 页面里面使用,不能再 components 组件里面用;
造成此限制的原因之一是 React 在渲染页面之前需要拥有所有必需的数据。

## nextjs 使用/api/路由和 getServerSideProps 的区别

都是处理服务器端请求的机制，但它们的使用场景和作用不同
/api/路由可以提供 GET,POST 等请求方式,也可以给外部使用;
getServerSideProps: 是在预渲染页面时使用,用途为在页面渲染之前获取服务器端的数据，并将其直接传递给页面组件。

## APP routing 和 Page routing 区别

https://segmentfault.com/a/1190000045123079
优先使用 page routing

## Handbook

### Image

有以下属性:

<Image src='/abc.jpg' alt='abc' width={400} height={400} placeholder="blur" [priority]/>

nextjs 加载器, 使得远程图片 /abc.jpg 可以运行
使用远程图片时候, 需要在 next.config.js

```js
module.exports = {
  images: {
    domains: ["example.com", "example2.com"],
  },
};
```

priority 属性: 可以使 nextjs 优先加载这个图像, 最好是页面中最大的那个图片
layout="fill": 填充容器,不知道图片尺寸

### useRoute

报错为只能在客户端渲染页面使用,如何确定此页面是客户端还是服务端的呢?
onClick={() => router.push('/sg')} right
onClick={router.push('/sg')} wrong
router.push 浏览器可以返回;
router.replace 浏览器不能返回;

## 常用的几个 Hook

- useState 用于声明状态变量。可在函数组件中保存和更新状态.  
     `const [count, setCount] = useState(0);`
- useEffect 用于管理副作用，如数据获取、订阅或手动更改 DOM。它在组件首次渲染后和依赖项更新时执行。  
     `useEffect(() => {})`
- useRoute 用于访问路由对象，获取当前路由信息并在客户端侧执行导航。  
     const router = useRouter();
- useContext 在组件树中共享数据而无需逐层传递。适用于全局状态管理，如主题或用户信息。  
     const theme = useContext(ThemeContext);
- useCallback 缓存函数定义，以便在依赖项未更改时保持同一引用，适用于子组件属性传递。
- useSWR 用于数据获取的钩子，支持缓存、重试和实时数据同步。它非常适合 Next.js 的数据拉取和客户端数据同步. 客户端渲染

## typewriter-effect 使用问题

```typescript
<TypewriterComponent
  onInit={() => {}}
  options={{
    strings: ["Chatbot.", "Code Generation.", "Photo Generation."],
    autoStart: true,
    loop: true,
  }}
/>
```

报错 Error: Super expression must either be null or a function；

出现 Error: Super expression must either be null or a function 错误，通常是因为在继承类时，继承的父类不是一个有效的函数或者是 null，这可能发生在 React 组件或其他 JavaScript 类继承中

## Q&A

1. useEffet 或者 useSWR 和 getServerSideProps() 使用场景
   在 Next.js 中，useEffect、useSWR 和 getServerSideProps 都是数据获取的工具，但它们的适用场景不同，取决于数据获取的时机、数据更新频率、SEO 需求以及性能考虑。以下是它们的使用场景和最佳实践。

2. APP routing 和 Page routing 区别
   https://segmentfault.com/a/1190000045123079

object-cover contain fill 区别

1. object-cover
   作用：object-cover 会让图片或视频按比例缩放并填满容器，但会裁剪掉超出容器的部分。
   实现效果：图像会完全覆盖容器，并保持原始的宽高比。图像会填满整个容器，但可能会有部分内容被裁剪。
   常用场景：适用于需要图片完全填满容器而不在意裁剪的情况，如全屏背景图或卡片封面图。

2. object-contain
   作用：object-contain 会让图片或视频按比例缩放，使其在容器内完全显示，但不会裁剪内容。
   实现效果：图像会根据容器大小缩放，以保证所有内容都在容器内显示。图像的宽高比保持不变，但可能会留有空白区域（比如上下或左右留白）。
   常用场景：适用于希望图片完全显示且不被裁剪的情况，如产品图片展示、缩略图。

3. object-fill
   作用：object-fill 会让图片或视频在容器内被拉伸或压缩，以完全填满容器。
   实现效果：图像会不保留原始的宽高比，被强行拉伸或压缩以适应容器的宽度和高度，因此可能会导致图像变形。
   常用场景：适用于必须完全填满容器的情况，且不介意图片变形的场景。
