<template>
  <div :class="{center: blocks}" class="card card-w70">
    <div v-if="blocks.length !== 0">
      <component
          :is="block.type"
          v-for="block in blocks"
          :key="block.id"
          :content="block.content"
          @remove-block="$emit('removeBlock', block.id)"
      ></component>
    </div>
    <h3 v-else>Добавьте свой первый блок. (Слева в меню)</h3>
  </div>
</template>

<script>
import AppHeader from "@/AppHeader";
import AppSubHeader from "@/AppSubHeader";
import AppAvatar from "@/AppAvatar";
import AppText from "@/AppText";

export default {
  emits: ['removeBlock'],
  props: {
    blocks: Array
  },
  components: {
    AppHeader,
    AppSubHeader,
    AppAvatar,
    AppText
  },
}
</script>
