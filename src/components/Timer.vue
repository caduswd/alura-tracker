<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Stopwatch :timeInSeconds="timeInSeconds" />
    <ActionButton
      :button="{
        label: 'play',
        icon: 'fas fa-play',
        class: '',
        disabled: stopwatchRunning
      }"
      @click="start"
    />
    <ActionButton
      :button="{
        label: 'stop',
        icon: 'fas fa-stop',
        class: '',
        disabled: !stopwatchRunning
      }"
      @click="stop"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Stopwatch from './Stopwatch.vue'
import ActionButton from './ActionButton.vue'

export default defineComponent({
  name: 'Timer',

  emits: ['finishedTimer'],

  components: {
    Stopwatch,
    ActionButton
  },

  data: () => ({
    timeInSeconds: 0,
    stopwatch: 0,
    stopwatchRunning: false
  }),

  methods: {
    start() {
      // 1 seg = 1000 ms
      this.stopwatchRunning = true
      this.stopwatch = setInterval(() => {
        this.timeInSeconds += 1
      }, 1000)
    },

    stop() {
      this.stopwatchRunning = false
      clearInterval(this.stopwatch)
      this.$emit('finishedTimer', this.timeInSeconds)
      this.timeInSeconds = 0
    }
  }
})
</script>
