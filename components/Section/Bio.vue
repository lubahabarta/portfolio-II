<script setup lang="ts">
const trigger = ref<null | HTMLDivElement>(null);

const props = defineProps<{ sc: number }>();
</script>

<template>
    <section id="bio" class="relative bg-red-500">
        <div ref="trigger"></div>
        <header class="sticky top-0 bg-green-500 h-[20vh]">
            {{ props.sc }}
        </header>
        <div class="h-[100vh] flex justify-center items-center">
            aaa
        </div>
        <div class="h-[100vh] flex justify-center items-center">
            aaa
        </div>
        <div class="h-[100vh] flex justify-center items-center">
            aaa
        </div>
        <div class="h-[100vh] flex justify-center items-center">
            aaa
        </div>
    </section>
</template>