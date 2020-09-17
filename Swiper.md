# swiper
## 安装引入
1. 安装
```
npm install swiper vue-awesome-swiper --save
```
2. 引入
```js
//swiper
import VueAwesomeSwiper from 'vue-awesome-swiper'
// If you use Swiper 6.0.0 or higher
import 'swiper/swiper-bundle.css'
import Swiper2, {
  Navigation, //前进后退
  Pagination, //分页器
  Autoplay, //自动切换
} from 'swiper'
Swiper2.use([Navigation, Pagination, Autoplay])
Vue.use(VueAwesomeSwiper, /* { default options with global component } */ )
```
## 使用
1. HTML部分
```html
<template>
  <div class="wrap wrap_login">
    <swiper ref="mySwiper" :options="swiperOptions">
      <swiper-slide class="bac1">Slide 1</swiper-slide>
      <swiper-slide class="bac2">Slide 2</swiper-slide>
      <swiper-slide class="bac3">Slide 3</swiper-slide>
      <swiper-slide class="bac4">Slide 4</swiper-slide>
      <swiper-slide class="bac5">Slide 5</swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>
  </div>
</template>
```
2. js部分
```js
//data里边
swiperOptions: {
    pagination: {
        el: ".swiper-pagination",
        clickable: true,
    },
    navigation: {
        nextEl: ".swiper-button-next",
        prevEl: ".swiper-button-prev",
    },
    loop: true,
    autoplay: {
        delay: 3000,
        stopOnLastSlide: false,
        disableOnInteraction: true,
    },
},
```