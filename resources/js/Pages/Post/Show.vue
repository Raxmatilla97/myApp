<template>
   
        <h1 class="text-lg mb-8">Posni ko'rish</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-sky-500 text-lg mb-8">Orqaga qaytish</Link>
        </div>
        
        <div v-if="post">
            <div class="mt-8 pt-8 border-t border-gray-400">
                <div>id: {{ post.id }}</div>
                <div>Nomlanishi: {{ post.title }}</div>
                <div>Asosiy qism: {{ post.content }}</div>
                <div class="text-sm text-right">Yaratilgan sana: {{ post.date }}</div>
            </div>
        </div>
  

</template>

<script>
import { Link } from '@inertiajs/vue3';
import MainLayoutVue from '@/Layouts/MainLayout.vue';
export default {
    name: "Index",

    layout: MainLayoutVue,

    props: [
        "post"
    ],

    components: {
        Link
    }
}
</script>

<style>

</style>