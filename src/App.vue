<template>
  <div>{{ formatedCountdown || 'countdown over' }}</div>
</template>

<script>
import * as moment from 'moment'
import 'moment-duration-format'

export default {
  data() {
    return {
      countdown: 300, // 5min
    }
  },
  mounted() {
    const stopCountdown = setInterval(() => {
      console.log('current countdown', this.countdown)
      this.countdown -= 1
      if (!this.countdown) clearInterval(stopCountdown)
    }, 1000)
  },
  computed: {
    formatedCountdown() {
      return moment.duration(this.countdown, 'seconds').format('m:ss')
    },
  },
}
</script>
