<template>
   
    <h1 class="text-lg mb-2">Yaratilgan postni tahrirlash</h1>
    <div class="mb-8">
        <Link :href="route('post.index')" class="text-sky-500 text-lg mb-8">Orqaga qaytish</Link>
    </div>
    
    <form @submit.prevent="update">
        <div class="mb-4">
            <input class="rounded-full border-gray-300 w-full" type="text" v-model="title" placeholder="title">
        </div>
        <div class="mb-4">
            <textarea class="rounded-full border-gray-300 w-full" type="text" v-model="content" placeholder="Content"></textarea>
        </div>
        <div class="mb-4">
            <button class=" ml-auto hover:bg-white hover:text-sky-500 border border-sky-500 block p-2 w-32 text-center text-white bg-sky-500 rounded-full" type="submit">Yangilash</button>
        </div>
    </form>

</template>

<script>
import { Link } from '@inertiajs/vue3';
import MainLayoutVue from '@/Layouts/MainLayout.vue';
export default {
name: "Index",
layout: MainLayoutVue,
components: {
    Link
},
props: [
    'post'
],
data() {
    return {
        id: this.post.id,
        title: this.post.title,
        content: this.post.content,
    }
},

methods: {
    update(){
        // console.log(this.title)
        this.$inertia.patch(`/posts/${this.id}`, {title: this.title, content: this.content})
    }
}
}
</script>

<style>

</style>