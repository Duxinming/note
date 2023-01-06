安装
npm i -S vue-navigation
使用
main.js 中
import Navigation from 'vue-navigation';
Vue.use(Navigation, {router})； // vue-router 实例

App.vue 中
<navigation>
<router-view></router-view>
</navigation>

![页面自动生成的刷新标识](https://upload-images.jianshu.io/upload_images/19978726-66a89f02f9f559c8.png?imageMogr2/auto-orient/strip|imageView2/2/w/742/format/webp)

如果有 vuex
Vue.use(Navigation, {router, store})
更改刷新的 Key
Vue.use(Navigation, {router,keyName: 'SSSS'})
![更改刷新的Key](https://upload-images.jianshu.io/upload_images/19978726-034373a8ce9a5b8d.png?imageMogr2/auto-orient/strip|imageView2/2/w/596/format/webp)

使用场景：

实现前进刷新，后退不刷新
前进、后退分别使用不同的过场动画。
vue-navigation 支持如下 5 种事件类型的监听：
forward：前进
back：后退
replace：替换
refresh：刷新
reset：重置
对应的监听方法：
this.$navigation.on('forward', (to, from) => {
console.log('forward to', to, 'from ', from)
})

作者：浅浅\_2d5a
链接：https://www.jianshu.com/p/8bd1972f7fa6
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
