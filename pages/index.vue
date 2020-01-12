<template>
  <div class="space">
    <Rocket class="rocket" />
  </div>
</template>

<script>
import Rocket from '~/assets/svg/rocket.svg?inline'

export default {
  components: {
    Rocket
  }
}
</script>

<style>
.space {
  @apply bg-black min-h-screen flex justify-center items-end pb-10;
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
