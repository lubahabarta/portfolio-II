<script setup>
const { items, reversed } = defineProps({
    items: {
        type: Array,
        required: true,
    },
    reversed: Boolean,
});
</script>

<template>
    <div class="w-full overflow-hidden mt-4">
        <div class="flex w-[calc((14vh+1rem)*20)] sm:w-[calc((28vh)*20)]" :class="reversed ? 'animate-reverseSlider' : 'animate-slider'">
            <SliderSkill v-for="item in items" :src="item.src" :alt="item.alt" />
            <SliderSkill v-for="item in items" :src="item.src" :alt="item.alt" />
        </div>
    </div>
</template>