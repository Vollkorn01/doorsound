<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div style="background-color: yellow;">
      <p>Motion Detected</p>
      <div>
        Acceleration Z: {{accelerationZ}}
      </div>
      {{playingSoundText}}
      <button @click.prevent="playSoundRestart()">Start</button>
      <button @click.prevent="handleMotion(event)">Simulate Motion</button>

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
      counter: 0,
      squeak_yes: new Audio(require('../assets/squeak-yes.mp3')),
      moan_mmh_yes: new Audio(require('../assets/moan-mmh-yes.mp3')),
      oh_yes: new Audio(require('../assets/oh-yes.mp3')),
      moan_aaah_likethat: new Audio(require('../assets/moan-aaah-likethat.mp3')),
      moan_yes_touchme: new Audio(require('../assets/moan-yes-touchme.mp3')),
      moan_yes_grabmyhandle: new Audio(require('../assets/moan-yes-grabmyhandle.mp3')),
      moan_shake_me: new Audio(require('../assets/moan-shake-me.mp3')),
      moan_yes_exactlylikethat: new Audio(require('../assets/moan-yes-exactlylikethat.mp3')),
      moan_faster_1: new Audio(require('../assets/moan-faster-1.mp3')),
      moan_faster_2: new Audio(require('../assets/moan-faster-2.mp3')),
      moan_moan: new Audio(require('../assets/moan-moan.mp3')),
      moan_yes: new Audio(require('../assets/moan-yes.mp3')),
      moan_yes_high: new Audio(require('../assets/moan-yes-high.mp3')),
      moan_high: new Audio(require('../assets/moan-high.mp3')),
      moan_higher: new Audio(require('../assets/moan-higher.mp3')),
      moan_highest: new Audio(require('../assets/moan-highest.mp3')),
      moan_orgasm: new Audio(require('../assets/moan-orgasm.mp3')),
      desinfect: new Audio(require('../assets/desinfect.mp3')),
      moan_afterorgasm: new Audio(require('../assets/moan-afterorgasm.mp3')),
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
    setTimeout( function () {
      window.addEventListener("devicemotion", this.handleMotion, true);
    }.bind(this), 3000);

    /*
     for each mp3, set 'soundIsPlaying' to false, so audios don't play over each other
     */
    this.squeak_yes.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_mmh_yes.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.oh_yes.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_aaah_likethat.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_yes_touchme.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_yes_grabmyhandle.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_shake_me.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_yes_exactlylikethat.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_faster_1.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_faster_2.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_moan.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_yes.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_yes_high.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_high.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_higher.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_highest.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_orgasm.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.desinfect.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));
    this.moan_afterorgasm.addEventListener("ended", function(){
      console.log("ended");
      this.playingSoundText = 'not playing sound'
      this.soundIsPlaying = false
    }.bind(this));

    // reset audio every 4 minutes
    window.setInterval(function () {
      this.counter = 0
    }.bind(this), 240000);
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
        this.counter += 1
      }
    },
    /*
      play test sound to enable sound and restart the counter
     */
    playSoundRestart () {
      this.counter = 0
      this.oh_yes.play()
    },
    /*
      playing moan sounds one after the other
    */
    playSound () {
      console.log('playingSound', this.counter)
        switch (this.counter) {
            case 0: this.squeak_yes.play()
                break
            case 1: this.moan_mmh_yes.play()
                break
/*            case 2: this.oh_yes.play()
                break*/
 /*           case 3: this.moan_aaah_likethat.play()
                break
            case 4:this.moan_yes_touchme.play()
                break*/
            case 2: this.moan_yes_grabmyhandle.play()
                break
/*            case 6: this.moan_shake_me.play()
                break*/
            case 3: this.moan_yes_exactlylikethat.play()
                break
            case 4: this.moan_faster_1.play()
                break
            case 5: this.moan_faster_2.play()
                break
/*            case 10: this.moan_moan.play()
                break
            case 11: this.moan_yes.play()
                break*/
            case 6: this.moan_yes_high.play()
                break
            case 7: this.moan_high.play()
                break
/*            case 14: this.moan_higher.play()
                break*/
/*            case 8: this.moan_highest.play()
                break*/
            case 8: this.moan_orgasm.play()
                break
/*            case 17: this.moan_afterorgasm.play()
                break*/
            case 9: this.desinfect.play()
                  this.counter = 0
            break
        }
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
