<script setup>
import { computed } from 'vue';
import { usePage } from '@inertiajs/inertia-vue3';

const errors = computed(() => usePage().props.value.errors);

const hasErrors = computed(() => Object.keys(errors.value).length > 0);
</script>

<template>
<TransitionGroup

   name="v" tag="dov"
  >
        <div v-if="hasErrors" class="w-full font-medium text-white font-mohave bg-error rounded-[30px] px-4 py-2 mt-2 mb-6 ">

 <div class="flex col justify-start mr-2  items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12 " fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z" />
                        </svg>
                        <div class="ml-2 leading-6 border-transparent border-solid  pl-2">

                            <div v-for="(error, key) in errors" :key="key" class= "">

            <div class="flex col"> {{ error }}</div>
        </div>
                        </div>
                    </div>






        </div>
</TransitionGroup>

</template>

<style scoped>
/* we will explain what these classes do next! */.v-enter-active,
.v-leave-active {
  transition: all 1s ease;
}
.v-enter-from,
.v-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>
