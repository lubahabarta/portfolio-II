<script setup lang="ts">
const { scrolled } = defineProps({
    scrolled: {
        type: Number,
        required: true,
    }
});

const s = (val: number) => {
    console.log(val);
};
</script>

<template>
    <section id="bio" class="relative bg-red-500">
        <header class="sticky top-0 bg-green-500 h-[20vh]">
            {{ s(scrolled) }}
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