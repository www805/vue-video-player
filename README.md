# vue

> vue this is vue

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run e2e tests
npm run e2e

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

### 1. 安装依赖
``` 
npm install vue-video-player --save
```
### 2. 在main.js引入vue-video-player

``` 
import VueVideoPlayer from 'vue-video-player'
Vue.use(VueVideoPlayer)
```
截图如下：
![](https://images2018.cnblogs.com/blog/1332575/201807/1332575-20180726200924775-726712209.jpg)

### 3. 编写myPlayer.vue组件，并引入其样式。
myPlayer.vue：

```
<template>
    <div class="player-container">
      <video-player class="vjs-custom-skin" :options="playerOptions"></video-player>
    </div>
</template>

<script>
//引入video样式
import 'video.js/dist/video-js.css'
import 'vue-video-player/src/custom-theme.css'

//引入hls.js
import 'videojs-contrib-hls.js/src/videojs.hlsjs'

export default {
  data () {
    return {
        playerOptions: {
            playbackRates: [0.7, 1.0, 1.5, 2.0], //播放速度
            autoplay: false, //如果true,浏览器准备好时开始回放。
            controls: true, //控制条
            preload: 'auto', //视频预加载
            muted: false, //默认情况下将会消除任何音频。
            loop: false, //导致视频一结束就重新开始。
            language: 'zh-CN',
            aspectRatio: '16:9', // 将播放器置于流畅模式，并在计算播放器的动态大小时使用该值。值应该代表一个比例 - 用冒号分隔的两个数字（例如"16:9"或"4:3"）
            fluid: true, // 当true时，Video.js player将拥有流体大小。换句话说，它将按比例缩放以适应其容器。
            sources: [{
                  type: 'application/x-mpegURL',
                  src: 'https://video-dev.github.io/streams/x36xhzz/x36xhzz.m3u8'
            }],
            poster: "http://static.smartisanos.cn/pr/img/video/video_03_cc87ce5bdb.jpg", //你的封面地址
            width: document.documentElement.clientWidth,
            notSupportedMessage: '此视频暂无法播放，请稍后再试' //允许覆盖Video.js无法播放媒体源时显示的默认信息。
          }
        }
  },
  methods: {
    
  },
  computed: {
    
  }
}
</script>

<style lang="scss">
  @import "@/assets/scss/player.scss";
</style>
```
### 4. 注意事项：

video-player标签的class必须设置成“video-player vjs-custom-skin”，你引入的样式才能起作用。
增加hls的支持。支持流媒体m3u8g等等格式播放。

### 5. 增加hls.js支持，故此要安装依赖，如下：

``` npm install --save videojs-contrib-hls ```

所以在myPlayer.vue 引入：
![](https://images2018.cnblogs.com/blog/1332575/201807/1332575-20180726201945464-1993896705.jpg)

### 6.  package.json 如下：
![](https://images2018.cnblogs.com/blog/1332575/201807/1332575-20180726202142911-1662219066.jpg)

### 7. 启动服务，查看效果
```npm run dev```
 
最终效果图：
![](https://images2018.cnblogs.com/blog/1332575/201807/1332575-20180726202528351-1518043547.jpg)

