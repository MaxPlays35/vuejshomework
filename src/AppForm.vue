<template>
  <form class="card card-w30" @submit.prevent="submitForm">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="typeOfBlock">
        <option value="Header">Заголовок</option>
        <option value="SubHeader">Подзаголовок</option>
        <option value="Avatar">Аватар</option>
        <option value="Text">Текст</option>
      </select>
    </div>

    <app-input v-model="content" :error="error"></app-input>

    <button :disabled="error" class="btn primary">Добавить</button>
  </form>
</template>

<script>
import AppInput from "@/AppInput";

export default {
  emits: ['submit'],
  data() {
    return {
      typeOfBlock: 'Header',
      content: '',
      valid: true
    }
  },
  components: {
    AppInput
  },
  computed: {
    error() {
      if (this.content.length < 3) {
        return 'Введите не менее 3 символа'
      } else {
        return null
      }
    }
  },
  methods: {
    submitForm() {
      if (!this.error) {
        this.$emit('submit', {
          type: 'App' + this.typeOfBlock,
          content: this.content
        })
        this.content = ''
      }
    }
  }
}
</script>

<style scoped>

</style>
