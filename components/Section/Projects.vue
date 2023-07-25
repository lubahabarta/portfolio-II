<script setup lang="ts">
const { scrolled } = defineProps({
    scrolled: {
        type: Number,
        required: true,
    }
});

const sectionRef = ref<null | HTMLDivElement>(null);
const listRef = ref<null | HTMLUListElement>(null);

const windowH = ref(0);
const windowW = ref(0);

const getListPosition = (s: number) => {
    if (s <= 0) {
        return `translateX(0)`;
    } else if (s > 0 && s <= sectionRef.value!.offsetHeight - windowH.value) {
        const percentage = (s) / (sectionRef.value!.offsetHeight - windowH.value);
        return `translateX(${(listRef.value!.offsetWidth - windowW.value) * percentage * -1}px)`;
    } else {
        return `translateX(${(listRef.value!.offsetWidth - windowW.value) * -1}px)`;
    }
};

onMounted(() => {
    windowH.value = window.innerHeight;
    windowW.value = window.innerWidth;
});
</script>

<template>
    <section ref="sectionRef" id="projects" class="h-[400vh] relative">
        <div class="sticky top-0 h-[100vh] w-full flex flex-col">
            <header class="h-1/4 w-full border-4 border-black">header</header>
            <div class="h-3/4 w-full overflow-hidden">
                <ul ref="listRef" class="h-full w-[450vw] md:w-[calc(50vw+3000px)] md: flex"
                    :style="{ transform: getListPosition(scrolled) }">
                    <li class="w-[50vw]"></li>
                    <li class="h-full w-[80vw] md:w-[600px] border-black bg-red-500 border-l-4 border-b-4"></li>
                    <li class="h-full w-[80vw] md:w-[600px] border-black border-l-4 border-b-4"></li>
                    <li class="h-full w-[80vw] md:w-[600px] border-black border-l-4 border-b-4"></li>
                    <li class="h-full w-[80vw] md:w-[600px] border-black border-l-4 border-b-4"></li>
                    <li class="h-full w-[80vw] md:w-[600px] border-black bg-green-500 border-l-4 border-b-4 border-r-4">
                    </li>
                </ul>
            </div>
        </div>
    </section>
</template>