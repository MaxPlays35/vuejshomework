<template>
  <div class="container column">
    <app-form @submit="sendForm"></app-form>
    <app-result
        :blocks="blocks"
        @remove-block="removeBlock"

    ></app-result>

  </div>

  <app-comments
      :comments="comments"
      :loading="loading"
      @load-comments="loadComments"
  ></app-comments>

</template>

<script>
import AppForm from "@/AppForm";
import AppResult from "@/AppResult";
import AppComments from "@/AppComments";
import axios from "axios";

export default {
  data() {
    return {
      blocks: [],
      comments: [],
      loading: false

    }
  },
  async mounted() {
    try {
      const {data} = await axios.get('https://vue-with-db-default-rtdb.firebaseio.com/blocks.json')

      this.blocks = Object.keys(data).map(id => {
        return {
          ...data[id],
          id
        }
      })
    } catch {
      this.blocks = []
    }


  },
  methods: {
    async loadComments() {
      this.loading = true
      const {data} = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')

      this.comments = data

      this.loading = false
    },
    async sendForm(formData) {
      const {data} = await axios.post('https://vue-with-db-default-rtdb.firebaseio.com/blocks.json', {
        ...formData
      })

      this.blocks.push({
        ...formData,
        id: data.name
      })
      console.log(this.blocks)
    },
    async removeBlock(id) {
      await axios.delete(`https://vue-with-db-default-rtdb.firebaseio.com/blocks/${id}.json`)


      this.blocks = this.blocks.filter(block => block.id !== id)
    }
  },
  components: {
    AppForm,
    AppResult,
    AppComments
  }
}
</script>

<style>
.inline {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
