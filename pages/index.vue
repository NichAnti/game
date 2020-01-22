<template>
  <div class="space">
    <Rocket :style="{ 'margin-bottom': rocketDistance }" class="rocket" />
  </div>
</template>

<script>
import Rocket from '~/assets/svg/rocket.svg?inline'

export default {
  components: {
    Rocket
  },

  data() {
    return {
      rocketDistance: 1,
      pushParam: 1.15,
      pullParam: 0.99
    }
  },

  mounted() {
    document.addEventListener('keydown', this.pushRocket)
    setInterval(this.pullRocket, 10)
  },

  destroyed() {
    document.addEventListener('keydown', this.pushRocket)
  },

  methods: {
    pushRocket() {
      if (this.rocketDistance * this.pushParam < window.innerHeight) {
        this.rocketDistance *= this.pushParam
      }
    },
    pullRocket() {
      if (this.rocketDistance >= 1) {
        this.rocketDistance *= this.pullParam
      }
    }
  }
}
</script>

<style>
.space {
  @apply bg-black h-screen flex justify-center items-end pb-10;
}

.rocket {
  width: 150px;
  animation-name: rocket-movement;
  animation-duration: 2s;
  animation-iteration-count: infinite;
}

@keyframes rocket-movement {
  0% {
    transform: translate3d(0px, 0px, 0px);
  }
  25% {
    transform: translate3d(-10px, 5px, 10px);
  }
  50% {
    transform: translate3d(5px, 10px, 5px);
  }
  75% {
    transform: translate3d(0px, 5px, 0px);
  }
  100% {
    transform: translate3d(0px, 0px, 0px);
  }
}
</style>
