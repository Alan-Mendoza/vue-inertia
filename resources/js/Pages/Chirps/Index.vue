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
import PrimaryButton from '@/Components/PrimaryButton.vue';
import { ref } from 'vue';
// import { Link } from '@inertiajs/vue3';
defineProps(['subtitle', 'title']);

const message = ref('');
function submitForm() {
    // console.log(message.value);
    axios.post(route('chirps.store'), { message: message.value })
    .then((res) => {
        console.log(res.data);
        message.value = ''; // limpiar el campo de texto
    })
}
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
                    <!-- {{ subtitle }}<br /> -->
                    <!-- <Link :href="route('chirps.index')">View Chirps</Link><br />
                    <Link :href="route('dashboard')">View Dashboard</Link><br /> -->
                    <form @submit.prevent="submitForm">
                        <textarea v-model="message" placeholder="What's on your mind?" class="block w-full rounded-md border-gray-300 bg-white focus:ring-indigo-500"></textarea>
                        <PrimaryButton class="mt-2">Chirp</PrimaryButton>
                    </form>
                </div>
            </div>
        </div>
    </AppLayout>
</template>