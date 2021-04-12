<template>
  <div class="main">
    <h1>Список уроков секции</h1>
    <div v-for="lesson in lessons" :key="lesson.idl">
      <nuxt-link :to="`/lesson/edit/${lesson.idl}`">
      {{ lesson.name_lesson }} - {{ lesson.descr }}
      </nuxt-link>
    </div>
  </div>
</template>

<script>
import axios from 'axios'   

export default {
  async asyncData({ $axios, params }) {
    const { data } = await $axios.get(`/api/lesson/readSection.php?ids=${params.ids}`)
    return { lessons: data }
  },

}
</script>
<style scoped>
.main {
  padding: 16px;
}
</style>