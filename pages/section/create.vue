<template>
  <div class="form">
       <h1>Добавить категорию</h1>
    <div class="form-element">
      <label for="name_section">Название категории:</label>
      <input type="text" v-model="name_section" id="name_section" />
    </div>
    <div class="form-element">
      <label for="type">Тип:</label>
      <input type="text" v-model="type" id="type" />
    </div>


    <div class="form-element">
      <label for="descr_section">Описание:</label>
      <textarea v-model="descr_section" id="descr_section" rows="4"></textarea>
    </div>
    <div>
      <button v-on:click="createSection">Отправить данные</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {

  data: () => ({
    name_section: "",
    type: "",
    descr_section: "",
  }),

  methods: {
    createSection() {
      let formData = {
        name_section: this.name_section,
        descr_section: this.descr_section,
        type: this.type
      };
      axios.post(`/api/section/create.php`, formData).then(

          setTimeout(() => {
              this.$router.push(`/section/`)
          }, 500)
          
      )
    },
  },
};
</script>

<style>
.form {
  width: 600px;
  margin: 0 auto;
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

