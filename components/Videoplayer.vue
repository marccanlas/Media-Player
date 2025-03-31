<template>
  <section class="container">
    <v-row  >
      <v-col cols="12" sm="12" md="12" style="margin-top:20%;">
        <div class="video-player-box"
            :playsinline="playsinline"
            @play="onPlayerPlay($event)"
            @pause="onPlayerPause($event)"
            @ended="onPlayerEnded($event)"
            @loadeddata="onPlayerLoadeddata($event)"
            @waiting="onPlayerWaiting($event)"
            @playing="onPlayerPlaying($event)"
            @timeupdate="onPlayerTimeupdate($event)"
            @canplay="onPlayerCanplay($event)"
            @canplaythrough="onPlayerCanplaythrough($event)"
            @ready="playerReadied"
            @statechanged="playerStateChanged($event)"
            v-video-player:myVideoPlayer="playerOptions">
        </div>
      </v-col>
    </v-row>


    <v-row  >
      <v-col cols="8" sm="8" md="8" style="margin-top:5%;">
        <input v-model="video_url" placeholder="video url" style="background-color:white;" size="100">
      </v-col>
      <v-col cols="4" sm="4" md="4" style="margin-left:1%;">
        <button v-on:click="loadVideo">Upload</button>
        <!-- <button v-on:click="ipfsLoad">Pinata</button> -->
      </v-col>
    </v-row>

  </section>
</template>

<script>
import 'video.js/dist/video-js.css'

  export default {
    data () {
      return {
        // component options
        // playsinline: true,
        video_url : "https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.webm",
        
        // videojs options
        playerOptions: {
          muted: true,
          language: 'en',
          controls: true,
          playbackRates: [0.7, 1.0, 1.5, 2.0],
          sources: [{
            type: "video/mp4",
            src: this.getVideoUrl()
          }],
          poster: "https://i.ytimg.com/vi/I5B1kxr2TQQ/maxresdefault.jpg",
        }
      }
    },
    mounted() {
      console.log('this is current player instance object', this.myVideoPlayer)
    },
    methods: {
      loadVideo(newUrl){
        console.log('Load new URL, ', this.playerOptions.sources)
        this.playerOptions.sources.push({
          type: "video/mp4",
            src: this.video_url
        })

      },
      ipfsLoad(){
        console.log('IPFS LOAD ')
      },
      getVideoUrl(){
        console.log('Load video URL', this.video_url )
        return "https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.webm";
      },
      // listen event
      onPlayerPlay(player) {
        // console.log('player play!', player)
      },
      onPlayerPause(player) {
        // console.log('player pause!', player)
      },
      onPlayerEnded(player) {
        // console.log('player ended!', player)
      },
      onPlayerLoadeddata(player) {
         console.log('player Loadeddata!', player)
      },
      onPlayerWaiting(player) {
        // console.log('player Waiting!', player)
      },
      onPlayerPlaying(player) {
        // console.log('player Playing!', player)
      },
      onPlayerTimeupdate(player) {
        console.log('player Timeupdate!', player.currentTime())
      },
      onPlayerCanplay(player) {
        // console.log('player Canplay!', player)
      },
      onPlayerCanplaythrough(player) {
        // console.log('player Canplaythrough!', player)
      },

      // or listen state event
      playerStateChanged(playerCurrentState) {
        console.log('player current update state', playerCurrentState)
      },

      // player is ready
      playerReadied(player) {
        console.log('example 01: the player is readied', player)
      }
    }
  }
</script>

<style lang="scss" scoped>
  .container {
    width: 60%;
    margin: 0 auto;
    padding: 50px 0;

    .video-player-box {
      min-height: 200px;
    }
  }
</style>