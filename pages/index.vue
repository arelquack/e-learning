<template>
    <div class="container mx-auto">
        <h1 class="text-4xl font-bold">Daftar Kursus</h1>
        <div class="grid grid-cols-3 gap-6 mt-4">
            <div v-for="course in courses" :key="course.id" class="p-4 border rounded-lg">
                <h2 class="text-xl font-semibold">{{ course.title }}</h2>
                <p class="text-gray-600">{{ course.description }}</p>
                <NuxtLink :to="`/courses/${course.id}`" class="mt-4 block text-blue-500">Lihat Kursus</NuxtLink>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const courses = ref([]);

onMounted(async () => {
    const response = await fetch('https://jsonplaceholder.typicode.com/posts');
    courses.value = await response.json();
});
</script>