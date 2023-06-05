<template>
    <div class="container mx-auto py-2">
      <h1 class="text-4xl font-bold">USER LIST</h1>
      <table class="table table-striped table-bordered shadow text-center mt-5">
            <thead>
              <tr class="text-white bg-primary">
            <th class="py-2 px-4 border-b">ID</th>
            <th class="py-2 px-4 border-b">Name</th>
            <th class="py-2 px-4 border-b">Email</th>
            <!-- <th class="py-2 px-4 border-b">Role</th> -->
          </tr>
        </thead>
        <tbody>
          <tr v-for="user in users.data" :key="user.id" class="border-b">
            <td class="py-4 px-6">{{ user.id }}</td>
            <td class="py-4 px-6">{{ user.name }}</td>
            <td class="py-4 px-6">{{ user.email }}</td>
          </tr>
        </tbody>
      </table>
      <div class="mt-6">
        <Pagination :links="users.links" />
      </div>
    </div>
  </template>
  
  <script setup>
    import AppLayout from "../../Layouts/AppLayout.vue"
    import Pagination from "../../Components/pagination.vue";
    import { defineProps } from 'vue'


    const props = defineProps({
        users: Object
    })
</script>
  <script>
  export default {
    layout: AppLayout,
    data() {
    return {
      message: '',
      users: [],
    };
  },
  props: {
      users: {
        type: Array,
        required: true
      }
    },
}
</script>