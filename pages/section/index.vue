<template>
  <div class="main">
    <h1>Список категорий</h1>
    <div v-for="section in sections" :key="section.ids">
      <nuxt-link :to="`/section/edit/${section.ids}`">
      {{ section.name_section }} - {{ section.descr_section }} -
      </nuxt-link>
      <nuxt-link :to="`/lesson/${section.ids}`">Список уроков ({{ section.count}})
      </nuxt-link>
      <button @click="deleteSection(section.ids)">X</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData() {
    const { data } = await axios.get(`/api/section/read.php`)
    return { sections: data }
  },
  methods: {
    deleteSection(ids) {
     // console.log(urlCategory)
      this.$axios
        .delete(`/api/section/delete.php?ids=${ids}`)
        .then(() => {
          setTimeout(() => {
            this.$router.push(`/section/`)
            console.log('___', this.$router.path)
          }, 500)
        })
        .catch((err) => console.log(err.response.data.message))
    },
  },
}
</script>
<style scoped>
.main {
  padding: 16px;
}
</style>