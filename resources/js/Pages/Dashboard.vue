<template>
    <app-layout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Dashboard
            </h2>
        </template>

        <div class="py-4">
            Dashboard
        </div>
    </app-layout>
</template>

<script>
    import AppLayout from '@/Layouts/Layout'

    export default {
        components: {
            AppLayout,
        },
    }
</script>
