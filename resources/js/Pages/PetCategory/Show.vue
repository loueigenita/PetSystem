<template>
  <div class="container py-8 mx-auto">
    <h1 class="mb-4 text-2xl font-bold">Pet Category Details</h1>

    <div class="row">
      <div class="col-md-4">
        <div class="bg-white rounded-lg shadow p-4">
          <p class="text-center " style="font-size: xx-large; text-transform: uppercase;">{{ petCategory.pet_species }}</p>
        </div>

        <div class="bg-white rounded-lg shadow-md p-4 mt-1">

          <p class="text-muted"> <strong class="text-dark">Animals</strong> do not ask for much in life, and most just need a warm, safe and sheltered place to live, as well as adequate food, water and exercise. In return they will give you unconditional love, loyalty and companionship. Dogs are a little more well known to offer unconditional love; cats can be a little fickle! But having a furry friend means you will always have a little living being, waiting patiently for you at home and ready to welcome you with a wagging tail or a purr.</p>
        </div>
      </div>

      <div class="col-md-8">
        <div class="bg-white rounded-lg shadow p-4">
          <h2 class="text-lg font-bold mb-2">Related Pets:</h2>
          <table class="table table-bordered table-striped shadow">
            <thead class="bg-primary text-center text-light">
              <tr>
                <th class="px-2 py-1">Name</th>
                <th class="px-2 py-1">Type</th>
                <th class="px-2 py-1">Color</th>
              </tr>
            </thead>
            <tbody class="text-center">
              <tr v-for="pet in petCategory.pets" :key="pet.id">
                <td class="px-2 py-1">{{ pet.pet_name }}</td>
                <td class="px-2 py-1">{{ pet.pet_type }}</td>
                <td class="px-2 py-1">{{ pet.pet_color }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import AppLayout from "../../Layouts/AppLayout.vue"
</script>

<script>
export default {
  layout: AppLayout,
  props: {
    petCategory: {
      type: Object,
      required: true,
    },
  },
  mounted() {
    console.log(this.petCategory);
  },
};
</script>
