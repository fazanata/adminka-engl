<template>
  <div class="form">
    <div class="form-element">
      <label for="name_lesson">Название урока</label>
      <input type="text" v-model="name_lesson" id="name_lesson" />
    </div>
    <div>
      <label for="section">Категория</label>
      <multiselect
        v-model="section"
        id="section"
        :options="sections"
        :multiple="false"
        placeholder="Выберите категорию"
        label="name_section"
        track-by="ids"
        selectLabel="Выбрать"
        deselectLabel="Убрать"
        selectedLabel="Выбрано"
        @input="onInputSelect"
      >
      </multiselect>
    </div>

    <div class="form-element">
      <label for="img_lesson">Изображение</label>
      <input type="text" v-model="img_lesson" id="img_lesson" />
    </div>
    <div class="form-element">
      <label for="descr_lesson">Описание урока</label>
      <textarea id="descr_lesson" v-model="descr_lesson" rows="4"></textarea>
    </div>

    <button @click="createLesson">Добавить урок</button>
  </div>
</template>

<script>
import axios from "axios";
import Multiselect from 'vue-multiselect'
export default {
  async asyncData({ $axios }) {
    const { data } = await $axios.get(`/api/section/read.php`)
    console.log('data sections =', data)
    return { sections: data }
  },
  data: () => ({
    name_lesson: '',
    img_lesson: '',
    descr_lesson: '',
  }),
  components: { Multiselect },
  methods: {
    onInputSelect(selectedItems) {
      console.log('section=', selectedItems)
    },
    createLesson() {
      let formData = {
        name_lesson: this.name_lesson,
        img_lesson: this.img_lesson,
        descr_lesson: this.descr_lesson,
        section: this.section.ids,
      }
      console.log('asds', formData)
      axios.post(`/api/lesson/create.php`, formData).then(
        setTimeout(() => {
          this.$router.push(`/lesson/`)
        }, 500)
      )
    },
  },
}
</script>
<style src="vue-multiselect/dist/vue-multiselect.min.css"></style>
<style>
.form {
  width: 600px;
}

.form-element {
  display: flex;
  flex-direction: column;
  margin-top: 16px;
}

.form-element input,
.form-element textarea {
  margin-top: 4px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>