<template>
  <div class="inline">
    <div class="avatar">
      <img :src="content">
    </div>
    <button class="btn danger" @click="$emit('removeBlock')">🧺</button>
  </div>
</template>

<script>
export default {
  props: ['content'],
  emits: ['removeBlock']
}
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
