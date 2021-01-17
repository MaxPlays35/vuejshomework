<template>
  <div class="inline">
    <p>{{ content }}</p>
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
