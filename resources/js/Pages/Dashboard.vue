<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import ParentCalendar from './ParentCalendar.vue';
import { Head } from '@inertiajs/inertia-vue3';
</script>

<template>
    <Head title="Dashboard" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Dashboard</h2>
        </template>

        
           <ParentCalendar></ParentCalendar>
        
    </AuthenticatedLayout>
</template>
