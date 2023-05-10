<template>
   
        <h1 class="text-lg mb-8">Postlar</h1>
        <div class="mb-8">
            <Link :href="route('post.create')" class="hover:bg-white hover:text-sky-500 border border-sky-500 block p-2 w-32 text-center text-white bg-sky-500 rounded-full"> Post qo'shish</Link>
        </div>
        <div v-if="posts">
            <div class="mt-8 pt-8 border-t border-gray-400" v-for="post in posts">
                <div>id: {{ post.id }}</div>
                <div>Nomlanishi: {{ post.title }}</div>
                <div>Asosiy qism: {{ post.content }}</div>
                <div class="text-sm text-right">Yaratilgan sana: {{ post.date }}</div>
                <div class="text-sm text-right">
                    <Link class="text-sky-500" :href="route('post.show', post.id)">Ko'rish</Link>
                </div>
                <div class="text-sm text-right">
                    <Link class="text-sky-500" :href="route('post.edit', post.id)">Tahrirlash</Link>
                </div>
                <div class="text-sm text-right">
                    <p class="cursor-pointer text-red-500"  @click="deletePost(post.id)">O'chirish</p>
                </div>
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
        "posts"
    ],

    components: {
        Link
    },

    methods: {
        deletePost(id) {
            this.$inertia.delete(`/posts/${id}`)
        }
    }
}
</script>

<style>

</style>