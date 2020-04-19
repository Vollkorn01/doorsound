<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div style="background-color: yellow;">
      <p>Motion Detected</p>
      <div>
        Acceleration Z: {{accelerationZ}}
      </div>
      {{playingSoundText}}
      <button @click.prevent="handleMotion(event)">Play Test Sound</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Moan',
  props: {
    msg: String
  },
  data() {
    return {
      accelerationZ: 0,
      soundIsPlaying: false,
      playingSoundText: 'not playing sound',
      audio: new Audio(require('../assets/moan_1.mp3')),
      event: {
        acceleration :
                {
                  z: 3
                }
      },
    }
  },
  created() {
    /*
    3 sec timeout before activating motion
    provides time to play sound manually (otherwise sound won't get activated'
     */
    setTimeout(function(){
      window.addEventListener("devicemotion", this.handleMotion, true);
      this.audio.addEventListener("ended", function(){
        console.log("ended");
        this.playingSoundText = 'not playing sound'
        this.soundIsPlaying = false
      }.bind(this));
    }.bind(this), 3000);
  },
  methods: {
    /*
    Gets called when device moves
     */
    handleMotion(event) {
      console.log('Motion detected')
      this.accelerationZ = Math.round(event.acceleration.z * 10) / 10;
      if ((this.accelerationZ > 0.3 || this.accelerationZ < -0.3) && !this.soundIsPlaying) {
        this.playingSoundText = 'playing sound'
        this.soundIsPlaying = true
        this.playSound()
      }
    },
    /*
    playing the moan sound
     */
    playSound () {
        this.audio.play();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
