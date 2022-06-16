<script setup>
import { onMounted, ref } from 'vue';

defineProps(['modelValue', 'type', 'placeholder']);

defineEmits(['update:modelValue']);

const input = ref(null);

onMounted(() => {
    // if (input.value.hasAttribute('autofocus')) {
    //     input.value.focus();
    // }


});
</script>

<template>
    <div class="
            relative
            focus-within:text-gray-400
            w-full text-light-grey-100
            ">
      <span class="absolute inset-y-0 left-0 flex items-center pl-2">
        <div type="submit" class="p-1 focus:outline-none focus:shadow-outline text-dark-900">
             <slot></slot>
        </div>
      </span>
      <input :type="type" name="q"

       :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"

      class="
            w-full
            rounded-full
            font-mohave
            text-md
            leading-1
            pt-3
            pl-11
            placeholder-light-gray-100
            text-light-gray-100
            bg-light-gray-300
            focus:outline-none
            focus:text-white" :placeholder="placeholder" autocomplete="off">

    </div>





</template>

<style scoped>
input[type='password'] {
    font-family: Verdana;
    letter-spacing: 0.125em;

}
::placeholder {
   font-family: Mohave;
   letter-spacing: 0em;
   font-weight: 500;

}
</style>
