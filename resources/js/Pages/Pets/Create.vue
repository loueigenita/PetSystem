
<template>
  <div class="center-create">
    <form class="form" @submit.prevent="submitForm">

      <div class="flex">
        <label>
          <input v-model="form.pet_name" name="pet_name" required="" placeholder="" type="text" class="input">
          <span>Pet Name</span>
        </label>
        <div v-if="errors.pet_name" class="text-sm italic text-red-500">{{ errors.pet_name[0] }}</div>

        <label>
          <input v-model="form.pet_type" name="pet_type" required="" placeholder="" type="text" class="input">
          <span>Pet Type</span>
        </label>
        <div v-if="errors.v - pet_type" class="text-sm italic text-red-500">{{ errors.pet_type[0] }}</div>
      </div>
      <label>
        <input v-model="form.pet_color" name="pet_color" required="" type="tel" placeholder="" class="input">
        <span>Pet Color</span>
      </label>

      <div v-if="errors.pet_color" class="text-sm italic text-red-500">{{ errors.pet_color[0] }}</div>

      <select class="input" v-model="form.petspecies_id" name="petspecies_id" placeholder="Pet Category">
        <option value="">Select Pet Category</option>
        <option v-for="category in petcategories" :value="category.id" :key="category.id">{{ category.pet_species }}
        </option>
      </select>
      <div v-if="errors.petspecies_id" class="text-sm italic text-red-500">{{ errors.petspecies_id[0] }}</div>

      <button type="submit" class="fancy" href="#">
        <span class="top-key"></span>
        <span class="text">create</span>
        <span class="bottom-key-1"></span>
        <span class="bottom-key-2"></span>
      </button>
    </form>
  </div>
</template>

<script setup>
import AppLayout from "../../Layouts/AppLayout.vue"


</script>
<script>
export default {
  layout: AppLayout,
  data() {
    return {
      form: {
        pet_name: '',
        pet_type: '',
        pet_color: '',
        petspecies_id: ''
      },
    };
  },
  props: {
    errors: Object,
    petcategories: Array, // Define the prop for the errors object
  },
  methods: {
    submitForm() {

      this.$inertia.post(('/pets/store'), this.form)
        .then(() => {
        })
        .catch((error) => {
          console.error(error);
        });
    }
  }
}
</script>
<style>
.center-create {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 350px;
  background-color: #fff;
  padding: 20px;
  border-radius: 10px;
  position: relative;
}

.message {
  color: rgba(88, 87, 87, 0.822);
  font-size: 14px;
}


.form label {
  position: relative;
}

.form label .input {
  width: 100%;
  padding: 10px 10px 20px 10px;
  outline: 0;
  border: 1px solid rgba(105, 105, 105, 0.397);
  border-radius: 5px;
}

.form label .input+span {
  position: absolute;
  left: 10px;
  top: 15px;
  color: grey;
  font-size: 0.9em;
  cursor: text;
  transition: 0.3s ease;
}

.form label .input:placeholder-shown+span {
  top: 15px;
  font-size: 0.9em;
}

.form label .input:focus+span,
.form label .input:valid+span {
  top: 30px;
  font-size: 0.7em;
  font-weight: 600;
}

.form label .input:valid+span {
  color: green;
}

.input01 {
  width: 100%;
  padding: 10px 10px 20px 10px;
  outline: 0;
  border: 1px solid rgba(105, 105, 105, 0.397);
  border-radius: 5px;
}

.form label .input01+span {
  position: absolute;
  left: 10px;
  top: 50px;
  color: grey;
  font-size: 0.9em;
  cursor: text;
  transition: 0.3s ease;
}

.form label .input01:placeholder-shown+span {
  top: 40px;
  font-size: 0.9em;
}

.form label .input01:focus+span,
.form label .input01:valid+span {
  top: 50px;
  font-size: 0.7em;
  font-weight: 600;
}

.form label .input01:valid+span {
  color: green;
}

.fancy {
  background-color: transparent;
  border: 2px solid #2600ff;
  border-radius: 0px;
  box-sizing: border-box;
  color: #0400ff;
  cursor: pointer;
  display: inline-block;
  font-weight: 390;
  letter-spacing: 2px;
  margin: 0;
  outline: none;
  overflow: visible;
  padding: 8px 30px;
  position: relative;
  text-align: center;
  text-decoration: none;
  text-transform: none;
  transition: all 0.3s ease-in-out;
  user-select: none;
  font-size: 13px;
}

.fancy::before {
  content: " ";
  width: 1.7rem;
  height: 2px;
  background: #556fff;
  top: 50%;
  left: 1.5em;
  position: absolute;
  transform: translateY(-50%);
  transform: translateX(230%);
  transform-origin: center;
  transition: background 0.3s linear, width 0.3s linear;
}

.fancy .text {
  font-size: 1.125em;
  line-height: 1.33333em;
  padding-left: 2em;
  display: block;
  text-align: left;
  transition: all 0.3s ease-in-out;
  text-transform: lowercase;
  text-decoration: none;
  color: #000000;
  transform: translateX(30%);
}

.fancy .top-key {
  height: 2px;
  width: 1.5625rem;
  top: -2px;
  left: 0.625rem;
  position: absolute;
  background: white;
  transition: width 0.5s ease-out, left 0.3s ease-out;
}

.fancy .bottom-key-1 {
  height: 2px;
  width: 1.5625rem;
  right: 1.875rem;
  bottom: -2px;
  position: absolute;
  background: white;
  transition: width 0.5s ease-out, right 0.3s ease-out;
}

.fancy .bottom-key-2 {
  height: 2px;
  width: 0.625rem;
  right: 0.625rem;
  bottom: -2px;
  position: absolute;
  background: white;
  transition: width 0.5s ease-out, right 0.3s ease-out;
}

.fancy:hover {
  color: white;
  background: #2600ff;
}

.fancy:hover::before {
  width: 1.5rem;
  background: white;
}

.fancy:hover .text {
  color: white;
  padding-left: 1.5em;
}

.fancy:hover .top-key {
  left: -2px;
  width: 0px;
}

.fancy:hover .bottom-key-1,
.fancy:hover .bottom-key-2 {
  right: 0;
  width: 0;
}
</style>
