<script setup>
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: Boolean,
    canRegister: Boolean,
    laravelVersion: String,
    phpVersion: String,
});
</script>

<template>
    <Head title="Welcome" />
    <div class="relative sm:flex sm:justify-center sm:items-center min-h-screen bg-dots-darker bg-center bg-gray-100 dark:bg-dots-lighter dark:bg-gray-900 selection:bg-red-500 selection:text-white">
      <div v-if="canLogin" class="sm:fixed sm:top-0 sm:right-0 p-6 text-right z-10">
        <template v-if="$page.props.auth.user">
          <Link :href="route('dashboard')" class="font-semibold text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500">
           DASHBOARD
          </Link>
        </template>
        <template v-else>
          <Link :href="route('login')">
            LOG IN
          </Link>
         
        </template>
      
      </div>
      <div class="container">
        <h1 class="h1 mb-5">WELCOME TO MY PET</h1>
        <p class="text-dark">Owning a pet can open up your world. If you have a dog, then you will have to walk it daily, which means that you will have interactions with other dog owners and walkers too. This can help with loneliness in people who find it difficult to make friends.</p>
    </div>
    </div>
  </template>
  
  
  

<style>

.container {
    text-align: center;
    margin-top: 10px;
}
.h1 {
    font-size: 38px;
    color: rgb(0, 0, 0);
    font-weight: 300;
    font-family: 'Times New Roman', Times, serif;
}
.btn1 {
    display: inline-block;
    padding: 12px 24px;
    background-color: #333;
    color: #fff;
    text-decoration: none;
    border-radius: 4px;
    font-size: 18px;
    transition: background-color 0.3s;
}
.btn1:hover {
    background-color: #666;
}
</style>
