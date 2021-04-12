<template>
  <div class="form">
    <div class="form-element">
      <label for="name_lesson">Название урока</label>
      <input type="text" id="name_lesson" />
    </div>
    <div>
      <label for="section">Категория</label>
      <multiselect
        id="section"
        :options="sections"
        :multiple="false"
        placeholder="Выберите категорию"
        label="name_section"
        track-by="ids"
        selectLabel="Выбрать"
        deselectLabel="Убрать"
        selectedLabel="Выбрано"
      >
      </multiselect>
    </div>
    <div class="form-element">
      <label for="img_lesson">Изображение</label>
      <input type="text" id="img_lesson" />
    </div>
    <div class="form-element">
      <label for="descr_lesson">Описание урока</label>
      <textarea id="descr_lesson" rows="4"></textarea>
    </div>

    <button @click="createLesson">Добавить урок</button>
  </div>
</template>

<script>
import Multiselect from 'vue-multiselect'
export default {
  async asyncData({ $axios }) {
    const { data } = await $axios.get(`/api/section/read.php`)
    console.log('data pages =', data)
    return { sections: data }
  },
  components: { Multiselect },
  methods: {
      createLesson() {
          
      }
  }
}
</script>
