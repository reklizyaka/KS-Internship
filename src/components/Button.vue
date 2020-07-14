<template>
  <button @click="callback($event)">{{ text }}</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: String
  },
  methods: {
    callback(e) {
      this.$emit('click', e);
    }
  }
}
</script>

<style scoped>
    button {
        padding: 4px 12px;
        border: 1px solid;
        background: transparent;
        cursor: pointer;
    }
</style>
