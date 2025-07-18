<!-- <script setup>
// const title = 'Title from Vue';
import MyLayout from '@/Layouts/MyLayout.vue';
    defineProps([
        'subtitle',
        'title'
    ]);
</script>
<template>
    <MyLayout>
            <h1>{{ title }}</h1>
        <h2>{{ subtitle }}</h2>
    </MyLayout>
</template> -->

<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import Welcome from '@/Components/Welcome.vue';
defineProps(['subtitle', 'title']);
</script>

<template>
    <AppLayout title="Chirps" :meta-description="subtitle">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                {{ title }}
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg p-5">
                    {{ subtitle }}
                </div>
            </div>
        </div>
    </AppLayout>
</template>