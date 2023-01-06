<template>
  <button class="button" @click="$emit('click')" :disabled="button.disabled">
    <span class="icon">
      <i :class="button.icon"></i>
    </span>
    <span>{{ button.label }}</span>
  </button>
</template>

<script>
export default {
  name: 'ActionButton',
  emits: ['click'],
  props: {
    button: {
      type: Object,
      default: () => ({
        label: '',
        class: '',
        icon: '',
        disabled: false
      })
    }
  },
  methods: {
    click() {
      this.$emit('click')
    }
  }
}
</script>

<style></style>
