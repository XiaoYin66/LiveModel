<template>
  <div class="hello">
    <videoPlayer :options="playerOptions" class="vis-custom-skin videoPlayer"></videoPlayer>
    <!-- <aliPlayer></aliPlayer> -->
  </div>
</template>

<script>
import { flashChecker } from "../assets/flash";
import aliPlayer from "./videoTest";
import "video.js/dist/video-js.css";
import { videoPlayer } from "vue-video-player";
import "videojs-flash";

export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      playerOptions: {
        height: "300",
        sources: [
          {
            type: "rtmp/flv",
            // type: "application/x-mpegURL",
            src: "rtmp://116.213.200.53/tslsChannelLive/PCG0DuD/live"
          }
        ],
        techOrder: ["flash"],
        notSupportedMessage: "视频无法播放",
        autoplay: true,
        controls: true
      }
    };
  },
  created() {
    var res = flashChecker();
    console.log("flash检测", res);
    if (res.f) {
      return;
    } else {
      if (confirm("您的浏览器未安装Flash插件，现在安装？")) {
        window.location.href = "https://www.flash.cn/";
      }
    }
  },
  components: {
    aliPlayer,
    videoPlayer
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
