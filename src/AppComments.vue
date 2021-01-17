<template>
  <div class="container">
    <p>
      <button class="btn primary" @click="$emit('loadComments')">Загрузить комментарии</button>
    </p>
    <div v-if="comments.length !== 0" class="card">
      <h2>Комментарии</h2>
      <ul class="list">
        <li v-for="comment in comments" :key="comment.id" class="list-item">
          <div>
            <p><strong>{{ comment.email }}</strong></p>
            <small>{{ comment.body }}</small>
          </div>
        </li>
      </ul>
    </div>
    <div v-if="loading" class="loader"></div>
  </div>
</template>

<script>

export default {
  props: ['comments', 'loading'],
  emits: ['loadComments']
}
</script>

<style scoped>

</style>
