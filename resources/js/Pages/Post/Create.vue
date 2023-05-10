<template>
   
        <h1 class="text-lg mb-2">Yangi post yaratish</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-sky-500 text-lg mb-8">Orqaga qaytish</Link>
        </div>
        
        <form @submit.prevent="store">
            <div class="mb-4">
                <input class="rounded-full border-gray-300 w-full" type="text" v-model="title" placeholder="title">
                <div v-if="errors.title" class="text-red-600 text-sm">{{ errors.title }}</div>
            </div>
            <div class="mb-4">
                <textarea class="rounded-full border-gray-300 w-full" type="text" v-model="content" placeholder="Content"></textarea>
                <div v-if="errors.content" class="text-red-600 text-sm">{{ errors.content }}</div>
            </div>
            <div class="mb-4">
                <button class=" ml-auto hover:bg-white hover:text-sky-500 border border-sky-500 block p-2 w-32 text-center text-white bg-sky-500 rounded-full" type="submit">Yuborish</button>
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
        'errors'
    ],
    data() {
        return {
            title: '',
            content: '',
        }
    },

    methods: {
        store(){
            this.$inertia.post('/posts', {title: this.title, content: this.content})
        }
    }
}
</script>

<style>

</style>