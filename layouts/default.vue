<template>
    <svg class="fixed top-0 w-full h-full z-[999] pointer-events-none opacity-70">
        <filter id="noise-filter">
            <feTurbulence type="fractalNoise" baseFrequency="1.3" />
        </filter>
        <rect width="100%" height="100%" filter="url(#noise-filter)" />
    </svg>
    <Navigation />
    <slot />
    <Footer />
</template>