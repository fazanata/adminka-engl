<template>
  <main>
    <h1>Справочники</h1>
    <h2>Категории</h2>
    <nuxt-link to="/section">Список категорий</nuxt-link>
    <nuxt-link to="/section/create">Добавить категорию</nuxt-link>
    <h2>Уроки</h2>
    <nuxt-link to="/lesson/create">Добавить урок</nuxt-link>
    <h2>Пользователи</h2>
    <nuxt-link to="/user">Список пользователей</nuxt-link>
    <hr/>

  </main>
</template>

<script>
export default {}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
