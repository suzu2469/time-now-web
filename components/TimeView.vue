<template>
  <div id="show-time">
    <div class="time-inner">
      <h1 class="time-row">
        {{ getMonth }}/{{ currentTime.getDate() }}
      </h1>
      <h1 class="time-row">
        {{ getHours }}&nbsp;<span class="time-coron">:</span>&nbsp;{{ getMinutes }}
      </h1>
    </div>
    <div class="fade-layer"></div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      currentTime: null
    }
  },
  created () {
    this.setCurrentTime()
    this.handleTime()
  },
  computed: {
    getHours () {
      return ('00' + this.currentTime.getHours()).slice(-2)
    },
    getMinutes () {
      return ('00' + this.currentTime.getMinutes()).slice(-2)
    },
    getSeconds () {
      return ('00' + this.currentTime.getSeconds()).slice(-2)
    },
    getMonth () {
      return this.currentTime.getMonth() + 1
    }
  },
  methods: {
    async handleTime () {
      const sleep = ms => new Promise(resolve => setTimeout(resolve, ms))
      while (true) {
        await sleep(1000)
        this.setCurrentTime()
      }
    },
    setCurrentTime () {
      this.currentTime = new Date
    }
  }
}
</script>

<style scoped>
.fade-layer {
  background-color: rgba(0, 0, 0, 0.4);
  content: '';
  display: block;
  position: fixed;
  top: 0;
  left: 0;  
  width: 100%;
  height: 100vh;
}
#show-time {
  height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  margin: 0;
  padding: 30px 0 0;
  background-image: url('../assets/img/wallpaper.jpg');
  background-repeat: no-repeat;
  background-position: top center;
  background-size: 850px 550px
}
.time-inner {
  position: relative;
  z-index: 5; 
  color: white;
}
.time-row {
  font-size: 120px;
  text-align: center;
  user-select: none;
  letter-spacing: 0.05em;
  line-height: 1.4em;
}
.time-coron {
  animation: flashing-in ease 2s infinite;
}

@keyframes flashing-in {
  0% {
    color: inherit;
  }
  50% {
    color: transparent;
  }
  100% {
    color: inherit;
  }
}
</style>

