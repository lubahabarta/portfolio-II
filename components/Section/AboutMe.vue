<template>
    <section id="about-me" class="w-full flex justify-center">
        <div class="w-[80vw]">
            <div class="w-full grid gap-[1.2px] grid-cols-1 sm:grid-cols-2 xl:grid-cols-3 bg-[radial-gradient(#9ca3af,rgba(0,0,0,0)60%)] bg-fixed">
                <div class="bg-white col-span-1 aspect-square centered">
                    <img src="/img/me.jpg" alt="me.jpg" class="w-full h-full object-cover" />
                </div>
                <div class="col-span-1 grid gap-[1.2px] grid-cols-3">
                    <div class="bg-white col-span-1 aspect-square"></div>
                    <div class="bg-white col-span-2 row-span-2 aspect-square centered-vertical">
                        <span class="text-[18vw] sm:text-[10vw] xl:text-[8vw] font-bold">20</span> let
                    </div>
                    <div class="bg-white col-span-1 aspect-square"></div>
                    <div class="bg-white col-span-1 aspect-square"></div>
                    <div class="bg-white col-span-1 aspect-square"></div>
                    <div class="bg-white col-span-1 aspect-square"></div>
                </div>
                <div class="bg-white col-span-1 flex items-center justify-center aspect-square">some text</div>
                <div class="col-span-1 grid gap-[1.2px] grid-cols-2">
                    <div class="bg-white col-span-1 aspect-square"></div>
                    <div class="bg-white col-span-1 aspect-square"></div>
                    <div class="bg-white col-span-1 aspect-square"></div>
                    <div class="bg-white col-span-1 aspect-square"></div>
                </div>
                <div class="bg-white col-span-1 aspect-square centered">
                    <img src="/img/me2.jpg" alt="me2.jpg" class="w-full h-full object-cover" />
                </div>
                <div class="bg-white col-span-1 flex items-center justify-center aspect-square">some text</div>
            </div>
        </div>
    </section>
</template>

<style scoped lang="scss">
.centered {
    @apply flex items-center justify-center p-[10%];
}

.centered-vertical {
    @apply flex flex-col items-center justify-center p-[10%]
}
</style>