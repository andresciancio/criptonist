<script setup>
import BreezeApplicationLogo from '@/Components/ApplicationLogo.vue';
import { Link } from '@inertiajs/inertia-vue3';

defineProps({
    canResetPassword: Boolean,

});
</script>

<template>
    <div
        class="min-h-screen flex flex-col sm:justify-center items-center pt-6 sm:pt-0 bg-dark-gray-900 bg-no-repeat bg-contain"
        style="background-image: url('/img/back.png')"
    >
    <div>
        <Link href="/">
                <BreezeApplicationLogo class="fill-current" />
        </Link>
    </div>
     <slot />


    </div>
</template>
