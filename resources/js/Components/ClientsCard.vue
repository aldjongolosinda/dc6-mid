<template>
    <div class="bg-gray-400 shadow-md p-2 rounded-lg mx-2">
        <div class="flex justify-center mb-5">
  <img
    src="https://costinteodor.github.io/CSS_Main_Assignment/images/unknownProfilePicture.jpg"
    alt="logo"
    class="logo-image bg-gray-400 shadow-md p-2 rounded-full mx-2"
  >
</div>

      <h3 class="text-sm font-semibold">{{ client.last_name }}, {{ client.first_name }}</h3>
      <p class="text-dark-700 text-xs">{{ client.address }}</p>
      <p>{{ client.phone }}</p>
      <span class="card-level mt-2 bg-black text-white px-2 py-1 rounded text-xs">

          Level {{ client.level }}
        </span>
        <a
            :href="'/clients/view/' + client.id"
            class="border-2 border-solid flex justify-center rounded-md border-gray-900 p-2"
            :class="{
                'bg-red-600': selectedColor == 'red',
                'bg-blue-600': selectedColor == 'blue',
                'bg-green-600': selectedColor == 'green',
            }"
        >Click me
        </a>
    </div>
</template>

<script setup>
import { defineProps } from "vue";
import { inject } from "vue";

const selectedColor = inject("selectedColor");
// const selectedColor = ref('')

const props = defineProps({
    client: Object,
});
</script>
