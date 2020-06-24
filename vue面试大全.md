# vue面试大全

#### 1.谈谈你对MVVM开发模式的理解

>Model：代表数据模型，数据和业务逻辑都在Model层定义
>
>View: 代表Ui视图，负责数据的展示
>
>ViewModel：负责监听Model中数据的改变且控制视图的更新，处理用户交互操作
>
>Model和View并无直接的关联，而是通过了ViewModel进行联系的，Model和ViewModel之间有着双向数据绑定的联系，因此，Model中的数据改变时会触发View层的刷新，View中由于交互操作而改变的数据也会在Model中同步
>
>这种模式实现了Model和View的数据自动同步，因此开发者只需要专注数据的维护操作即可，而不需要自己操作dom

#### 2.V-if和V-show有什么区别

>v-show仅仅控制元素的显示方式，将display属性在block和none来回切换，而v-if会控制这个dom节点的存在与否，当我们需要经常地切换某个元素的显示/隐藏时，会使用v-show会更加省性能上的开销，当需要一次显示或隐藏时，使用v-if 更加合理

#### 3.vue.js的两个核心是什么

>数据驱动和组件系统
>
>数据驱动： ViewModel，保证数据和视图的一致性
>
>组件系统：应用类UI可以看作全部是由组件树构成的

#### 4.vue的优点

>轻量级框架
>
>只关注视图层,是一个构建数据的视图集合,大小只有几十kb
>
>Vue.js通过简洁的API提供高效的数据绑定和灵活的组件系统
>
>视图,数据,结构分离:使数据的更改更为简单,不需要进行逻辑代码的修改,只需要操作数据就能完成相关操作

#### 5.vue的生命周期

>1.beforeCreate
>
>这个钩子是new Vue()之后触发的第一个钩子，在当前阶段中data、methods、computed以及watch上的数据和方法均不能被访问。
>
>2.created
>
>这个钩子在实例创建完成后发生，当前阶段已经完成了数据观测，也就是可以使用数据，更改数据，在这里更改数据不会触发updated函数。可以做一些初始数据的获取，在当前阶段无法与Dom进行交互，如果你非要想，可以通过vm.$nextTick来访问Dom。
>
>3.beforeMount
>
>这个钩子发生在挂载之前，在这之前template模板已导入渲染函数编译。而当前阶段虚拟Dom已经创建完成，即将开始渲染。在此时也可以对数据进行更改，不会触发updated。
>
>4.mounted
>
>这个钩子在挂载完成后发生，在当前阶段，真实的Dom挂载完毕，数据完成双向绑定，可以访问到Dom节点，使用`$refs`属性对Dom进行操作。也可以向后台发送请求，拿到返回数据。
>
>5.beforeUpdate
>
>这个钩子发生在更新之前，也就是响应式数据发生更新，虚拟dom重新渲染之前被触发，你可以在当前阶段进行更改数据，不会造成重渲染。
>
>6.updated
>
>这个钩子发生在更新完成之后，当前阶段组件Dom已完成更新。要注意的是避免在此期间更改数据，因为这可能会导致无限循环的更新。
>
>7.beforeDestroy
>
>这个钩子发生在实例销毁之前，在当前阶段实例完全可以被使用，我们可以在这时进行善后收尾工作，比如清除计时器。
>
>8.destroyed
>
>这个钩子发生在实例销毁之后，这个时候只剩下了dom空壳。组件已被拆解，数据绑定被卸除，监听被移出，子实例也统统被销毁。
>

#### 6.用于构建vue的vue-cli工程都用了那些技术，它们的作用分别是什么？

>1.vue.js: vue-cli工程的核心，主要特点是双向数据绑定和组件系统
>
>2.vue-router: vue官方推荐使用的路由框架
>
>3.vuex: 专为vue.js应用项目的状态管理器，主要用于维护vue组件间共用的一些变量和方法
>
>4.axios(fetch.ajax): 用于发起GET.或post等http请求，基于Promise设计
>
>5.vuex :一个专为vue设计的移动端UI组件库，
>
>6.创建一个emit.js文件，用于vue事件机制管理
>
>7.webpack: 模块加载和vue-cli工程打包器

#### 7.vue-cli 工程常用的 npm 命令有哪些？

>1. npm install：下载 node_modules 资源包的命令
>
>2. npm run dev： 启动 vue-cli 开发环境的 npm命令
>
>3. npm run build： vue-cli 生成 生产环境部署资源 的 npm命令
>
>4. npm run build--report： 用于查看 vue-cli 生产环境部署资源文件大小的 npm命令

#### 8.谈一下vue-cli工程中每个文件夹和文件的用处？

>1.dist 文件夹：默认 npm run build 命令打包生成的静态资源文件，用于生产部署。
>
>2.node_modules：存放npm命令下载的开发环境和生产环境的依赖包。
>
>3.public：有的叫assets：存放项目中需要用到的资源文件，css、js、images以及index
>
>4.src文件夹：存放项目源码及需要引用的资源文件。
>
>5.src-api文件夹：放ajax相关操作的代码文件:index.js(相关的接口),ajax.js(封装的axios,拦截器)。有的叫 service：自己配置的vue请求后台接口方法。
>
>6.src-common文件夹：stylus的混合文件.styl，不要写到public也可以
>
>7.src-components文件夹：存放vue开发中抽离的一些公共组件。
>
>8.src-mock文件夹：mock数据存放文件及mock模拟接口（没有后台接口或接口不完整情况下可以模拟后台接口）
>
>9.src-pages文件夹：涉及到路由的组件
>
>10.src-router文件夹:vue-router，路由器及路由的配置
>
>11.src-store文件夹：存放 vue中的状态数据，用vuex集中管理
>
>12.App.vue文件：使用标签渲染整个工程的.vue组件。
>
>13.main.js文件：vue-cli工程的入口文件。
>
>14.package.json文件：用于 node_modules资源部 和 启动、打包项目的 npm 命令管理。

#### 9.vue常用的修饰符

>1.阻止冒泡：.stop
>
>2.阻止默认事件：.prevent
>
>3.添加事件侦听器时使用事件捕获模式 ：.capture
>
>4.只当事件在该元素本身（比如不是子元素）触发时触发回调：.self
>
>5.事件只触发一次：.once

#### 10.说一下vue的双向绑定数据的原理

>VUEvue 实现数据双向绑定主要是：采用数据劫持结合 “发布者 - 订阅者”模式的方式，通过 Object.defineProperty() 来劫持各个属性的 setter、 getter，在数据变动时发布消息给订阅者，触发相应监听回调。
>
>