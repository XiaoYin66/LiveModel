<template>
  <div >
    <vue-aliplayer
      @ready="handleReady"
      ref="VueAliplayerV2"
      :options="options"
    />
    <button @click="play()">播放</button>
    <button @click="pause()">暂停</button>
    <button @click="replay()">重播</button>
    <button @click="getCurrentTime()">播放时刻</button>
  </div>
</template>
<script>
import VueAliplayer from "vue-aliplayer-v2";
export default {
  data() {
    return {
      options: {
        //配置项
        source: "rtmp://live.chosun.gscdn.com/live/tvchosun1.stream"
      }
    };
  },
  components: {
    VueAliplayer
  },
  methods: {
    /**
     * 在这里需要注意的是  this.$refs 可能会返回是数组,或者对象,这个在用的时候需要注意一下.且因为是异步渲染dom,所以最好是在 this.$nextTick(()=>{ //todo }); 里面调用
     * 事件可以参考文档 https://help.aliyun.com/document_detail/125572.html?spm=a2c4g.11186623.6.1085.36fc6fc57WKZ5P#h2-u64ADu653Eu5668u4E8Bu4EF63
     */
    play() {
        
      this.$refs.VueAliplayerV2.play();
    },

    pause() {
      this.$refs.VueAliplayerV2.pause();
    },

    replay() {
      this.$refs.VueAliplayerV2.replay();
    },

    getCurrentTime() {
      this.$refs.VueAliplayerV2.getCurrentTime();
    },

    /**
     * 播放器事件回调
     */
    handleReady(e) {
      console.log(`ready`, e);
    }
  },
  
};
</script>
<style lang="less" scoped>
* {
  margin: 0;
  padding: 0;
}
.player-btns {
  width: 800px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  span {
    margin: 0 auto;
    display: inline-block;
    padding: 5px 10px;
    width: 150px;
    height: 40px;
    line-height: 40px;
    border: 1px solid #eee;
    background: #e1e1e1;
    border-radius: 10px;
    text-align: center;
    margin: 20px auto;
    cursor: pointer;
  }
}
</style>