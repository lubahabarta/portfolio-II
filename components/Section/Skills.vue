<script setup>
const slider = {
    first: [
        { src: '/img/logos/html.png', alt:"html" },
        { src: '/img/logos/css.png', alt:"css" },
        { src: '/img/logos/javascript.png', alt:"javascript" },
        { src: '/img/logos/typescript.png', alt:"typescript" },
        { src: '/img/logos/node.png', alt:"node" },
        { src: '/img/logos/react.png', alt:"react" },
        { src: '/img/logos/redux.png', alt:"redux" },
        { src: '/img/logos/vite.png', alt:"vite" },
        { src: '/img/logos/vue.png', alt:"vue" },
        { src: '/img/logos/svelte.png', alt:"svelte" },
    ],
    second: [
        { src: '/img/logos/sass.png', alt:"sass" },
        { src: '/img/logos/tailwind.png', alt:"tailwind" },
        { src: '/img/logos/nuxt.png', alt:"nuxt" },
        { src: '/img/logos/nette.png', alt:"nette" },
        { src: '/img/logos/php.png', alt:"php" },
        { src: '/img/logos/firebase.png', alt:"firebase" },
        { src: '/img/logos/mysql.png', alt:"mysql" },
        { src: '/img/logos/git.png', alt:"git" },
        { src: '/img/logos/github.png', alt:"github" },
        { src: '/img/logos/bitbucket.png', alt:"bitbucket" },
    ],
    third: [
        { src: '/img/logos/cs.png', alt:"cs" },
        { src: '/img/logos/photoshop.png', alt:"photoshop" },
        { src: '/img/logos/illustrator.png', alt:"illustrator" },
        { src: '/img/logos/vue.png', alt:"vue" },
        { src: '/img/logos/nuxt.png', alt:"nuxt" },
        { src: '/img/logos/svelte.png', alt:"svelte" },
        { src: '/img/logos/tailwind.png', alt:"tailwind" },
        { src: '/img/logos/react.png', alt:"react" },
        { src: '/img/logos/javascript.png', alt:"javascript" },
        { src: '/img/logos/typescript.png', alt:"typescript" },
    ],
};
</script>

<template>
    <section id="skills" class="w-full h-[100vh] my-[10vh] flex justify-center">
        <div class="w-[80vw] flex flex-col justify-around">
            <div>
                asdf
            </div>
            <div class="relative content-none
                before:h-full before:w-10 before:absolute before:left-0 before:top-0 before:bg-gradient-to-r before:from-white before:to-transparent before:z-10
                after:h-full after:w-10 after:absolute after:right-0 after:top-0 after:bg-gradient-to-l after:from-white after:to-transparent after:z-10">
                <Slider :items="slider.first" />

                <Slider :items="slider.second" reversed />

                <Slider :items="slider.third" />
            </div>
        </div>
        </section>
    </template>