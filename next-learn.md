https://github.com/sanidhyy/discord-clone

https://github.com/mckaywrigley/chatbot-ui

https://github.com/shadcn-ui/ui

https://github.com/antfu/vue-minesweeper

---

## nextjs 中的常用的 hook

#### useState

组件通常需要根据交互更改屏幕上显示的内容.

useState Hook 提供了这两个功能：

- State 变量 用于保存渲染间的数据。
- State setter 函数 更新变量并触发 React 再次渲染组件。

你可以用 useState Hook 为组件添加状态。Hook 是能让你的组件使用 React 功能的特殊函数（状态是这些功能之一）。useState Hook 让你声明一个状态变量。它接收初始状态并返回一对值：当前状态，以及一个让你更新状态的设置函数。

Hook 是特殊的函数，只在 React 渲染时有效

设置它并不改变你已有的状态变量，而是触发一次重新渲染。

**设置 state 只会为下一次渲染变更 state 的值**

`一个 state 变量的值永远不会在一次渲染的内部发生变化`， 即使其事件处理函数的代码是异步的。

```js
console.log(count) // 0
setCount(count + 1) // 请求用 1 重新渲染
console.log(count) // 仍然是 0！
```

设置状态会请求一个新的重新渲染，但不会在已运行的代码中更改它.

```js
console.log(count) // 0
setCount((count) => count + 1) // 请求用 1 重新渲染
console.log(count) // 仍然是 0！
```

设置状态时传递一个 _更新器函数_ 来解决这个问题

State 是隔离且私有的。换句话说，如果你渲染同一个组件两次，每个副本都会有完全隔离的 state！改变其中一个不会影响另一个。

有两个方法可以在它们相互切换时重置 state，不切换组件位置，重置组件的状态：

- 将组件渲染在不同的位置
- 使用 key 赋予每个组件一个明确的身份 `<div key='taler'`

#### useReducer 随着组件复杂度的增加，你将很难一眼看清所有的组件状态更新逻辑，reducer 解决这个问题

#### createContext、useContext

你会通过 props 将信息从父组件传递到子组件。但是，如果你必须通过许多中间组件向下传递 props，或是在你应用中的许多组件需要相同的信息，传递 props 会变的十分冗长和不便。Context 允许父组件向其下层无论多深的任何组件提供信息

#### useRef

当你希望组件“记住”某些信息，但又不想让这些信息 触发新的渲染 时，你可以使用 ref 。

ref 是一个普通的 JavaScript 对象，具有可以被读取和修改的 `current` 属性。

`组件不会在每次递增时重新渲染。` 与 state 一样，React 会在每次重新渲染之间保留 ref。但是，设置 state 会重新渲染组件，更改 ref 不会！

当一条信息用于`渲染`时，将它保存在 state 中。当一条信息仅被`事件处理器`需要，并且更改它`不需要重新渲染`时，使用 ref 可能会更高效。

#### useEffect

Effect 允许你在渲染结束后执行一些代码

每当你的组件渲染时，React 会先更新页面，然后再运行 useEffect 中的代码。

默认情况下，Effect 会在 每次 渲染后运行。但往往 这并不是你想要的：

- 有时，它可能会很慢。与外部系统的同步并不总是即时的，所以你可能希望在不必要时跳过它。
- 有时，它可能会出错。

需要指定第二个依赖参数，通常为一个数组；依赖数组可以包含多个依赖项。只有当你指定的 所有 `依赖项的值都与上一次渲染时完全相同`，React 才会跳过重新运行该 Effect。

空数组，只会在组件第一次渲染时执行；

## nextjs 和 react 的关系及优势

## react 和 VUE

## 状态管理的组件

1. localStroage
2. reduxe
3. zustand

## 静态、动态渲染

## app router 和 pages router 优劣

## React Tips

#### 子组件事件传播

事件处理函数还将捕获任何来自子组件的事件。通常，我们会说事件会沿着树向上“冒泡”或“传播”：它从事件发生的地方开始，然后沿着树向上传播。

e.stopPropagation 可以阻止传播

#### 阻止默认行为

某些浏览器事件具有与事件相关联的默认行为。例如，点击 <form> 表单内部的按钮会触发表单提交事件，默认情况下将重新加载整个页面：

e.preventDefault 解决

不要混淆 e.stopPropagation() 和 e.preventDefault()。它们都很有用，但二者并不相关：

- e.stopPropagation() 阻止触发绑定在外层标签上的事件处理函数。
- e.preventDefault() 阻止少数事件的默认浏览器行为。 常用在 form 表单 handle 事件处理函数里面

## UI-Button + Link 组合时，

要使用`<Button>`包裹`<Link>`，这样上下间距的样式才会生效，比如父元素的`sapce-y-5`.

## sidebar flex-1 不能放到最下面 && icon color 不能显示

```ts
;<div className='mt-8 space-y-1 px-3 flex-1'>
  {SidebarTools.map((item) => (
    <Link
      key={item.name}
      href={item.href}
      className={cn(
        'flex p-3 rounded-lg text-sm hover:bg-white/10 hover:text-white items-center w-full font-medium transition',
        pathname === item.href ? 'bg-white/10 text-white' : 'text-zinc-400'
      )}
    >
      <div className='flex gap-x-3'>
        <item.icon className={cn('h-5 w-5', item.color)} />
        {item.name}
      </div>
    </Link>
  ))}
</div>

{
  /* pro */
}
;<div className='px-6'>isPro</div>
```

1. 需要在父元素里面添加 h-full，即可以修复`isPro`不在下面问题；

2. SidebarTools 在 config.ts 里需要加上 `as const`

```ts
const SidebarTools = [
  ...
] as const
```

`as const` 是 TypeScript 中的一个关键字组合，用于将变量声明为常量，并且会影响`类型推断`的方式.

## shadcn From 用法 包裹关系；

1. Form
2. FormField render=（）方法里面
   1. FormItem
      1. FormControl
         1. Input

## Button 组件的 Menu 不能调整大小

1. Button 里面添加 asChild;
2. 使用 !h-8，使用！强制覆盖样式；

## 添加 asChild 后，button 按钮变小

## prismaClient 新的用法

PrismaClient 是 Prisma 的核心类，用于与数据库进行交互。以下是 PrismaClient 的用法：
prisma 从 6 开始后，需要使用新的方法来创建 prismaclient 实例：

```js
import { PrismaClient } from '@prisma/client'
```

schema.prisma

```bash
generator client {
  provider = "prisma-client-js"
  output = "../lib/generated/prisma-client"
}
```

/lib/db.ts

```js
import { PrismaClient } from '@/lib/generated/prisma-client'
```

## node.js Promise 用法

```js
const prom = new Promise((resolve, reject) => {
  setTimeout(() => {
    const rad = Math.random()

    rad > 0.5 ? resolve('success') : reject('failed')
  }, 1000)
})

prom.then(
  (data) => {
    console.log('succ ', data)
  },
  (err) => {
    console.error('Err ', err)
  }
)
```

Promise 是一个对象，它可以获取异步操作的消息。是异步编程的一种方案

Promise 两个参数

1. resolve: 执行成功时候的方法；
2. reject： 执行失败的方法；

Promise 三个状态

pending： 初始等待

fullfiled： 成功，执行 resolve 函数；

rejected： 失败，执行 reject 函数；

调用
promise.then(resolve, reject)
OR
promise.then(resolve).catch(reject)

promise.finally() 异步任务成功与否，都执行

#### 参数是一个 Promise 数组

Promise.all([]) 全部成功提交

Promise.race([]) 谁先出结果用哪个；

## Zod 用法

Zod 是一个以 TypeScript 为首的模式声明和验证库 ，弥补了 TypeScript 无法在`运行时进行校验的问题`

Zod 既可以用在服务端也可以运行在客户端

Zod 经常被用于校验未知的 API 返回内容

Zod 是一个强大的库，特别适合用于类型安全的验证和数据解析。它的 API 非常直观且功能强大，可以用于表单验证、API 响应解析、数据清洗等多种场景

ChatGPT 用法很详细；

## aria-disabled 属性

辅助技术互联网应用）属性，用于向屏幕阅读器等辅助技术表明某个元素是禁用的，并且无法与用户交互

## nextjs 什么是 hook、provider、modal

#### Hook

本质上是内置在 React 中的特殊函数，它可以允许我们连接到 React 的一些内部机制，换句话说，Hooks 是一些公开内部响应功能的 API

Hook 是 React 16.8 引入的一个功能，使得你能够在函数组件中使用状态（useState）、生命周期方法（useEffect）以及其他功能，而不需要使用类组件。

定义通常使用 use 开头

#### Provider

Provider 是一种 React 组件，用于将上下文数据传递给子组件（类似 layout 组件）。通过上下文，你可以避免“层层传递”props 的困扰，而直接在组件树的较高层级定义`全局状态或配置`，并让下层的组件直接访问这些值。

使用场景：

- 共享全局状态：如认证状态、主题颜色、语言设置等。

- 通过上下文将值传递给组件树中的多个组件，而无需在每一层都通过 props 传递。

#### Modal

Modal 是一种弹出层，通常用于展示重要信息或提供额外的交互。它通常在当前页面上层显示，且不会跳转到其他页面。Modal 组件可以用于显示表单、确认对话框、图片、通知等内容。

## zustand 状态管理工具

zustand 是一个精简、快速、可扩展的状态管理器，特别契合 react hook 下开发。使用上非常简单，在一些特殊场景下也能优雅适配。是我目前使用过之后最喜欢的一个状态管理器

在 Zustand 中，create 是一个核心函数，用于创建你的 Zustand store。它接收一个状态创建函数作为参数，并返回一个 store API，你可以通过这个 API 来访问和修改 store 的状态。

[he](https://juejin.cn/post/7203262276572823609)

## SPA MCP

### spa single page application

### mcp model context protocol

## DO NOT COMMIT

This directory is auto-generated from `@clerk/nextjs` because you are running in Keyless mode. Avoid committing the `.clerk/` directory as it includes the secret key of the unclaimed instance.

---

## main Layout 不显示

uploadthing 使用的 `import "@uploadthing/react/styles.css"` 问题，修改 tailwind.config.ts 使用 withUt 一样出错误

## invite-modal 获取不到 useModal 的 server；

```ts
const { type, onOpen, isOpen, onClose, data } = useModal()
const server = { data }
```

> `const server = { data }` 错误，正常应该为`const { server } = data`

### Modal 变量的原理

## useOrigin 的 hook

hook 的本质就是全局方法?

## navigator.clipboard 用法

`navigator.clipboard.writeText(inviteUrl)`

> 使用在非 HTTPS 环境不能使用，本地调试也需要使用 localhost 或者 127.0.0.1 才行，不能使用自定义的主机名 Host

## query-string 用法

```ts
const url = qs.stringifyUrl({
  url: `/api/members/${memberId}`,
  query: {
    serverId: server?.id,
  },
})

const response = await axios.patch(url, { role })
```

### 对应 route.ts 用法

- const {allParams} = new URL(req.url); const serverId = allParams.get('serverId') 获取的数据是 url 里面 query 的东西，相当于参数；

- const { role } = await req.json() 获取的数据是 body 里面的数据，url 外的第二个{role}数据

用法也是有不小区别
