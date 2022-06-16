<script setup>
import CriptoButton from '@/Components/Button.vue';
import CriptoGuestLayout from '@/Layouts/Guest.vue';
import CriptoInput from '@/Components/Input.vue';
import CriptoLabel from '@/Components/Label.vue';
import CriptoValidationErrors from '@/Components/ValidationErrors.vue';
import { Head, Link, useForm } from '@inertiajs/inertia-vue3';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
    terms: false,
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<template>
    <CriptoGuestLayout>
        <div class="w-full sm:max-w-[400px] mt-6 px-6 py-4 bg-panel-bg shadow-md overflow-hidden sm:rounded-[40px]">
         <Head title="Register" />
            <div class="pt-4 text-center font-mohave font-medium text-2xl text-primary mb-8">

                Create an  criptonist account
            </div>


            <CriptoValidationErrors class="mb-4" />

            <form @submit.prevent="submit">
                <div>
                    <CriptoInput id="name" type="text" placeholder="Your name" class="mt-1 mb-6 block w-full" v-model="form.name" required autofocus  >
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
                            </svg>
                    </CriptoInput>
                </div>
       <div>

           <CriptoInput id="email" type="text" placeholder="Email" class="mt-1 mb-6 block w-full" v-model="form.email" required autofocus  >
                   <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                        </svg>
           </CriptoInput>
       </div>
       <div>


                            <CriptoInput id="password" type="password" placeholder="Password" class="mb-6"  v-model="form.password" required autofocus  >
                               <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                   <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 7a2 2 0 012 2m4 0a6 6 0 01-7.743 5.743L11 17H9v2H7v2H4a1 1 0 01-1-1v-2.586a1 1 0 01.293-.707l5.964-5.964A6 6 0 1121 9z" />
                               </svg>
                           </CriptoInput>
       </div>
       <div>


           <CriptoInput id="password_confirmation" type="password" placeholder="Password Confirmation" class="mb-6"  v-model="form.password_confirmation" required autofocus  >
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 7a2 2 0 012 2m4 0a6 6 0 01-7.743 5.743L11 17H9v2H7v2H4a1 1 0 01-1-1v-2.586a1 1 0 01.293-.707l5.964-5.964A6 6 0 1121 9z" />
              </svg>
          </CriptoInput>
       </div>

                <div class="flex items-center justify-end mt-4">


                    <CriptoButton  :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                        Register
                    </CriptoButton>
                </div>
            </form>

            <div>


    </div>
        </div>





               <div  class=" text-center mt-4 font-mohave font-medium text-primary">


               <Link :href="route('login')" class="hover:text-light-gray-300">
                Already registered?
            </Link>


            </div>
    </CriptoGuestLayout>


</template>
