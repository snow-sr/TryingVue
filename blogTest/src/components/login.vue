<template>
  <main>
    <div class="h-screen flex justify-center items-center">
      <!--Login-->
      <section class="text-gray-600 body-font relative">
        <div class="container px-5 py-24 mx-auto">
          <div class="flex flex-col text-center w-full mb-12">
            <h1
              class="
                sm:text-3xl
                text-2xl
                font-medium
                title-font
                mb-4
                text-gray-900
              "
            >
              Login.vue
            </h1>
            <p class="lg:w-2/3 mx-auto leading-relaxed text-base">
                Login based in mongo + vue, using axios to reach the server.
            </p>
          </div>
          <div class="lg:w-1/2 md:w-2/3 mx-auto">
            <div class="flex flex-wrap -m-2">
              <div class="p-2 w-1/2">
                <div class="relative">
                  <label for="name" class="leading-7 text-sm text-gray-600"
                    >Name</label
                  >
                  <input
                    type="text"
                    id="name"
                    name="name"
                    class="
                      w-full
                      bg-gray-100 bg-opacity-50
                      rounded
                      border border-gray-300
                      focus:border-indigo-500
                      focus:bg-white
                      focus:ring-2
                      focus:ring-indigo-200
                      text-base
                      outline-none
                      text-gray-700
                      py-1
                      px-3
                      leading-8
                      transition-colors
                      duration-200
                      ease-in-out
                    "
                    v-model="user.info.name"
                  />
                </div>
              </div>
              <div class="p-2 w-1/2">
                <div class="relative">
                  <label for="email" class="leading-7 text-sm text-gray-600"
                    >Email</label
                  >
                  <input
                    type="email"
                    id="email"
                    name="email"
                    class="
                      w-full
                      bg-gray-100 bg-opacity-50
                      rounded
                      border border-gray-300
                      focus:border-indigo-500
                      focus:bg-white
                      focus:ring-2
                      focus:ring-indigo-200
                      text-base
                      outline-none
                      text-gray-700
                      py-1
                      px-3
                      leading-8
                      transition-colors
                      duration-200
                      ease-in-out
                    "
                    v-model="user.info.email"
                  />
                </div>
              </div>
              <div class="p-2 w-full">
                <div class="relative">
                  <label for="password" class="leading-7 text-sm text-gray-600"
                    >password</label
                  >
                  <input
                    id="message"
                    type='password'
                    name="password"
                    class="
                      w-full
                      bg-gray-100 bg-opacity-50
                      rounded
                      border border-gray-300
                      focus:border-indigo-500
                      focus:bg-white
                      focus:ring-2
                      focus:ring-indigo-200
                      h-10
                      px-3
                      text-base
                      outline-none
                      text-gray-700
                      transition-colors
                      duration-200
                      ease-in-out
                    "
                    v-model="user.info.password"
                  />
                </div>
              </div>
              <div class="p-2 w-full">
                <button
                  class="
                    flex
                    mx-auto
                    text-white
                    bg-indigo-500
                    border-0
                    py-2
                    px-8
                    focus:outline-none
                    hover:bg-indigo-600
                    rounded
                    text-lg
                  "
                  @click="login"
                >
                    Submit
                </button>
              </div>
              <div
                class="
                  p-2
                  w-full
                  pt-8
                  mt-8
                  border-t border-gray-200
                  text-center
                "
              >
                <a class="text-indigo-500">Snow sr @ 2022</a>
                <p class="leading-normal my-3">
                    &copy; 2022. All rights reserved.
                </p>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </main>
</template>

<script>
import axios from "axios";
import {ref} from "vue";
export default {

  user: ref({
    info: {
      name: "",
      email: "",
      password: ""
    },
    logged: false
  }),


  data() {
    return {
        user,
    };
  },

  methods: {
    login: function() {
        console.log(this.user.info);
        axios.post('http://0.0.0.0:8087/login', this.user.info).then(result => console.log(result));
    }
  },

};
</script>
