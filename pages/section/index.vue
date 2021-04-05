<template>
    <div class="main">
        <h1>Список категорий</h1>
        <div v-for="section in sections" :key="section.ids">
                <nuxt-link :to="`/section/edit/${section.ids}`">{{ section.name_section}} - {{ section.descr_section}}  </nuxt-link>
        </div>
       
    </div>
</template>

<script>
import axios from "axios";

export default {

    async asyncData() {
        const {data} = await axios.get(`${process.env.baseUrl}/section/read.php`)
        return { sections: data}
    }
}
</script>
<style scoped>
.main {
    padding: 16px;
}
</style>