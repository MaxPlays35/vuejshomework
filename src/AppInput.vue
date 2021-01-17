<template>
  <div :class="{invalid: error}" class="form-control">
    <label for="value">Значение</label>
    <textarea id="value" :value="modelValue" rows="3" @input="change"></textarea>
    <small v-if="error">{{ error }}</small>
  </div>
</template>

<script>
export default {
  emits: ['update:modelValue'],
  props: {
    modelValue: String,
    error: String
  },
  methods: {
    change(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style scoped>

</style>
