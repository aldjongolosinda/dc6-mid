<script setup>
import Layout from "@/Layouts/Layout.vue";
import { Head } from "@inertiajs/vue3";

const props = defineProps({});
</script>

<template>
    <Head title="Create User" />
    <Layout title="Create User">
        <div class="flex justify-between ">
            <h2 class="font-bold text-4xl text-white ml-8 mt-4 mb-4">
                Create User
            </h2>
        </div>
    </Layout>
</template>
