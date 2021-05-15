<template>
  <div class="about">
    <video-player ref="playerObj"></video-player>
    <a @click="playVideo">播放视频</a>
  </div>
</template>
<script>
  import VideoPlayer from './VideoPlayer.vue'
  export default {
      name: 'about',
      components: {
          VideoPlayer
      },
      data() {
          return {}
 
      },
      methods: {
          playVideo() {
			//    没有监控流，先不开发。
              this.$refs['playerObj'].videoSrc = 'rtmp://xxxxxxxx'
              this.$refs['playerObj'].playerOptions.sources[0].src = 'rtmp://xxxxxxxx'
          }
      }
  }
</script>