<template>

  <v-row justify="left" align="left">
    <v-col cols="12" sm="8" md="6">
      <div>

       <p>  </p>
       <Video  ref="vPlayer" v-bind:video_url="video_url"></Video>

    

      </div>

    </v-col>
  </v-row>

</template>

<script>

import Video from '../components/Videoplayer.vue'


export default {
  name: 'HomePage',

  data () 
  {
    return {
      // component options
      playsinline: true,
      counter : 1,
      video_url : 'https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.mp4'

    }
  },
  methods: {
   onClick : function(){
     console.log('Onclick event' )
     vm.$refs.foo.loadVideo();
   }
  },
  components: {
    Video
  },

}
</script>