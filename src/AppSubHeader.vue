<template>
  <div class="inline">
    <h2>{{ content }}</h2>
    <button class="btn danger" @click="$emit('removeBlock')">🧺</button>
  </div>
</template>

<script>
export default {
  props: {
    content: String
  },
}
</script>
