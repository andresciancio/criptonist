<script setup>
import CriptoButton from '@/Components/Button.vue';
import CriptoCheckbox from '@/Components/Checkbox.vue';
import CriptoGuestLayout from '@/Layouts/Guest.vue';
import CriptoInput from '@/Components/Input.vue';
import CriptoLabel from '@/Components/Label.vue';
import CriptoValidationErrors from '@/Components/ValidationErrors.vue';
import { Head, Link, useForm } from '@inertiajs/inertia-vue3';

defineProps({
    canResetPassword: Boolean,
    status: String,
});

const form = useForm({
    email: '',
    password: '',
    remember: false
});

const submit = () => {

    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

<template>
    <CriptoGuestLayout :canResetPassword="canResetPassword">
      <div class="w-full sm:max-w-[400px] mt-6 px-6 py-4 bg-panel-bg shadow-md overflow-hidden sm:rounded-[40px]">


          <Head title="Log in" />
          <div class="pt-4 text-center font-mohave font-medium text-3xl text-primary">
              Welcome back!
          </div>
          <div class="text-center font-mohave font-medium text-2xl text-light-gray-300 leading-4">
              Sign in to your account
          </div>




          <div v-if="status" class=" font-medium text-sm text-green-600">
              {{ status }}
          </div>
          <div class="pt-4 px-4">
             <CriptoValidationErrors class="mb-4"/>
              <form @submit.prevent="submit">
                  <CriptoInput id="email" type="email" placeholder="Email" class="mt-1 mb-6 block w-full" v-model="form.email" required autofocus  >
                      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                      </svg>
                  </CriptoInput>

                  <CriptoInput id="password" type="password" placeholder="Password" class="mb-2"  v-model="form.password" required autofocus  >
                      <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 7a2 2 0 012 2m4 0a6 6 0 01-7.743 5.743L11 17H9v2H7v2H4a1 1 0 01-1-1v-2.586a1 1 0 01.293-.707l5.964-5.964A6 6 0 1121 9z" />
                      </svg>
                  </CriptoInput>

                  <div class="w-full  flex justify-end pr-4 mt-0 pt-0">
                      <label>
                          <CriptoCheckbox name="remember" v-model:checked="form.remember" class="bg-light-gray-300 align-text-top" />
                              <span class="ml-2 text-sm text-light-gray-300 hover:text-light-gray-100 font-mohave font-medium antialiased align-text-top">Remember me</span>
                      </label>
                  </div>

                  <CriptoButton class="mt-6 font-medium"  :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                      Log in
                  </CriptoButton>
              </form>
          </div>
      </div>
        <div  v-if="canResetPassword" class=" text-center mt-4 font-mohave font-medium text-primary">
        <div>
            <span class="text-white">
                    Don`t have an account?
                  </span>  <Link  :href="route('register')" class="hover:text-light-gray-300">
                        Sign up
                    </Link>
               </div>

                <Link v-if="canResetPassword" :href="route('password.request')" class="hover:text-light-gray-300">
                    Forgot your password?
                </Link>


            </div>
    </CriptoGuestLayout>
</template>
