<template>
  <section id="time-page">
    <time-view class="time-view" />
  </section>
</template>

<script>
import TimeView from '~/components/TimeView.vue'

export default {
  components: {
    TimeView
  }
}
</script>

<style scoped>
.time-view {
  margin-top: 25px;
}
</style>
