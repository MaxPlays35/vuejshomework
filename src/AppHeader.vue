<template>
  <div class="inline">
    <h1>{{ content }}</h1>
    <button class="btn danger" @click="$emit('removeBlock')">🧺</button>
  </div>
</template>

<script>
export default {
  props: {
    content: String
  },
  emits: ['removeBlock']
}
</script>

<style scoped>
.inline {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
