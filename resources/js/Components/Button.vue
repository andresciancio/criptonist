<script setup>
defineProps({
    type: {
        type: String,
        default: 'submit',
    },
});
</script>

<template>
    <button :type="type" class="
    w-full

    items-center
    py-2
    bg-dark-gray-900

    rounded-full
    font-mohave  text-md text-white   hover:bg-primary hover:text-dark-gray-900 active:bg-gray-900 focus:outline-none focus:border-gray-900 focus:shadow-outline-gray transition ease-in-out duration-150">
        <slot />
    </button>
</template>
