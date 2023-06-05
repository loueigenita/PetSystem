<template>
    <div class="container py-8 mx-auto">
      <h1 class="text-4xl font-bold">PET CATEGORIES</h1>

      <div class="flex justify-start mt-4">
        <Link
          :href="route('petcategories.create')"
          class="btn btn-m btn-primary mb-2"
        >
          <i class="fas fa-plus"></i>
        </Link>
      </div>
      <table class="table table-bordered table-striped shadow">
        <thead class="text-center bg-primary">
          <tr>
            <th class="px-4 py-2 border-b">Pet Species</th>
            <th class="px-4 py-2 border-b">Actions</th>
          </tr>
        </thead>
        <tbody>
          <template v-for="category in petspecies" :key="category.id">
            <tr>
              <td class=" text-center">{{ category.pet_species }}</td>
              <td class="text-center">
                <div class="flex justify-center space-x-2">
                  <Link :href="`/petcategories/show/${category.id}`">
                    <button class="btn btn-sm btn-success">
                      <i class="fas fa-eye"></i>
                    </button>
                  </Link>
                  <Link :href="`/petcategories/edit/${category.id}/`">
                    <button class="btn btn-sm btn-warning">
                     <i class="fas fa-pencil"></i>
                    </button>
                  </Link>
                </div>
              </td>
            </tr>
          </template>
        </tbody>
      </table>
    </div>
  </template>


  <script setup>

import AppLayout from "../../Layouts/AppLayout.vue"
  import { Link } from '@inertiajs/vue3'


</script>

  <script>

  export default {
    props: {
      petspecies: Array,
    },
    layout: AppLayout,
  };


  </script>
