<script setup>
import { Head, Link, useForm } from '@inertiajs/vue3';
import AuthenticationCard from '@/Components/AuthenticationCard.vue';
import AuthenticationCardLogo from '@/Components/AuthenticationCardLogo.vue';
import Checkbox from '@/Components/Checkbox.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';

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
  <Head title="Register" />

  <AuthenticationCard>
    <form action="" class="form_main" @submit.prevent="submit">
      <p class="heading">REGISTER</p>

      <div class="inputContainer">
        <svg class="inputIcon" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#2e2e2e"
          viewBox="0 0 16 16">
          <path
            d="M7.208 1.249c1.66 0 3 1.34 3 3.001s-1.34 3.001-3 3.001-3-1.34-3-3.001 1.34-3.001 3-3.001zm0 1c-1.104 0-2 .895-2 2s.896 2 2 2 2-.895 2-2-.896-2-2-2zm0 10c-2.757 0-5.152-1.422-6.543-3.563-.136-.256-.212-.551-.212-.86 0-1.655 1.346-3 3-3 1.264 0 2.362.785 2.801 1.875h1.398c.438-1.09 1.537-1.875 2.801-1.875 1.654 0 3 1.345 3 3 0 .309-.076.604-.211.86-1.39 2.14-3.784 3.563-6.542 3.563zm0-8.001c-1.656 0-3 1.343-3 3.001s1.344 3.001 3 3.001 3-1.343 3-3.001-1.344-3.001-3-3.001z" />
        </svg>
        <input type="text" name="name" v-model="form.name" placeholder="Enter Name" class="inputField" id="Name">
      </div>


      <InputError class="mt-1" :message="form.errors.name" />
      <div class="inputContainer">
        <svg class="inputIcon" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#2e2e2e"
          viewBox="0 0 16 16">
          <path
            d="M13.106 7.222c0-2.967-2.249-5.032-5.482-5.032-3.35 0-5.646 2.318-5.646 5.702 0 3.493 2.235 5.708 5.762 5.708.862 0 1.689-.123 2.304-.335v-.862c-.43.199-1.354.328-2.29.328-2.926 0-4.813-1.88-4.813-4.798 0-2.844 1.921-4.881 4.594-4.881 2.735 0 4.608 1.688 4.608 4.156 0 1.682-.554 2.769-1.416 2.769-.492 0-.772-.28-.772-.76V5.206H8.923v.834h-.11c-.266-.595-.881-.964-1.6-.964-1.4 0-2.378 1.162-2.378 2.823 0 1.737.957 2.906 2.379 2.906.8 0 1.415-.39 1.709-1.087h.11c.081.67.703 1.148 1.503 1.148 1.572 0 2.57-1.415 2.57-3.643zm-7.177.704c0-1.197.54-1.907 1.456-1.907.93 0 1.524.738 1.524 1.907S8.308 9.84 7.371 9.84c-.895 0-1.442-.725-1.442-1.914z">
          </path>
        </svg>
        <input type="email" name="email" v-model="form.email" class="inputField" id="Email" placeholder="Email">
      </div>
      <InputError class="mt-1" :message="form.errors.email" />
      <div class="inputContainer">
        <svg class="inputIcon" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#2e2e2e"
          viewBox="0 0 16 16">
          <path
            d="M8 1a2 2 0 0 1 2 2v4H6V3a2 2 0 0 1 2-2zm3 6V3a3 3 0 0 0-6 0v4a2 2 0 0 0-2 2v5a2 2 0 0 0 2 2h6a2 2 0 0 0 2-2V9a2 2 0 0 0-2-2z">
          </path>
        </svg>
        <input name="password" v-model="form.password" type="password" class="inputField" id="password"
          placeholder="Password">
      </div>
      <div class="inputContainer">
        <svg class="inputIcon" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#2e2e2e"
          viewBox="0 0 16 16">
          <path
            d="M8 1a2 2 0 0 1 2 2v4H6V3a2 2 0 0 1 2-2zm3 6V3a3 3 0 0 0-6 0v4a2 2 0 0 0-2 2v5a2 2 0 0 0 2 2h6a2 2 0 0 0 2-2V9a2 2 0 0 0-2-2z">
          </path>
        </svg>
        <input type="password" class="inputField" name="password_confirmation" v-model="form.password_confirmation"
          placeholder="Confirm password">
      </div>



      <button id="button">Submit</button>
      <p class="signup-link">
        No account?
        <Link :href="route('login')">login up here</Link>
      </p>
      <a class="forgotLink" href="#">Forgot your password?</a>
    </form>
  </AuthenticationCard>
</template>
<style>
.form_main {
  width: 350px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: rgb(255, 255, 255);
  padding: 30px 30px 30px 30px;
  box-shadow: 0px 0px 40px rgba(0, 0, 0, 0.062);
  position: relative;
  overflow: hidden;
}

.form_main::before {
  position: absolute;
  content: "";
  width: 300px;
  height: 300px;
  background-color: rgb(209, 193, 255);
  transform: rotate(45deg);
  left: -180px;
  bottom: 30px;
  z-index: 1;
  border-radius: 30px;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.082);
}

.heading {
  font-size: 2em;
  color: #2e2e2e;
  font-weight: 700;
  margin: 5px 0 10px 0;
  z-index: 2;
}

.inputContainer {
  width: 100%;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2;
}

.inputIcon {
  position: absolute;
  left: 3px;
}

.inputField {
  width: 100%;
  height: 30px;
  background-color: transparent;
  border: none;
  border-bottom: 2px solid rgb(173, 173, 173);
  margin: 10px 0;
  color: black;
  font-size: .8em;
  font-weight: 500;
  box-sizing: border-box;
  padding-left: 30px;
}

.inputField:focus {
  outline: none;
  border-bottom: 2px solid rgb(199, 114, 255);
}

.inputField::placeholder {
  color: rgb(80, 80, 80);
  font-size: 1em;
  font-weight: 500;
}

#button {
  z-index: 2;
  position: relative;
  width: 100%;
  border: none;
  background-color: rgb(162, 104, 255);
  height: 30px;
  color: white;
  font-size: .8em;
  font-weight: 500;
  letter-spacing: 1px;
  margin: 10px;
  cursor: pointer;
}

#button:hover {
  background-color: rgb(126, 84, 255);
}

.forgotLink {
  z-index: 2;
  font-size: .7em;
  font-weight: 500;
  color: rgb(44, 24, 128);
  text-decoration: none;
  padding: 8px 15px;
  border-radius: 20px;
}</style>