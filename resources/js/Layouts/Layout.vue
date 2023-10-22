<script setup>
import MainNav from "@/Components/MainNav.vue";
import { useDark, useToggle } from "@vueuse/core";
import { ref, provide } from "vue";
import { Link } from "@inertiajs/vue3";

let width = ref("w-[220px]");
let hide = ref(false);
const selectedColor = ref("");
const isDark = useDark();
const toggleDark = useToggle(isDark);

provide("selectedColor", selectedColor);

function toggleWidth() {
    if (width.value == "w-[220px]") {
        width.value = "w-[100px]";
        hide.value = true;
    } else {
        width.value = ["w-[220px]"];
        hide.value = false;
    }
}
</script>

<template>
    <div class="flex min-h-screen">
        <div
            id="sidebar"
            class="bg-gray-500 p-6 duration-500"
            :class="
                ([width],
                {
                    'bg-red-600': selectedColor == 'red',
                    'bg-blue-600': selectedColor == 'blue',
                    'bg-green-600': selectedColor == 'green',
                })
            "
            style="position: relative"
        >
            <button
                class="text-xl text-white"
                @click="toggleWidth"
                style="position: absolute; right: 10px; top: 10px"
            >
                <i class="fa-solid fa-bars"></i>
            </button>
            <div id="branding" :hidden="hide">
                <img
                    src="https://scontent.fceb1-3.fna.fbcdn.net/v/t39.30808-6/336257333_555031126610315_2677896213364470090_n.jpg?_nc_cat=104&ccb=1-7&_nc_sid=5f2048&_nc_eui2=AeHo0dAZz8LYmw9K8J3x6l7f2QcEp38DJ0bZBwSnfwMnRonWjBv4dwF3sP6q28DoUQDejNjaJ4ih5OFNpE4C5mSx&_nc_ohc=SNd8ehlc1YQAX_1V0ow&_nc_zt=23&_nc_ht=scontent.fceb1-3.fna&oh=00_AfAmVEyFT3-ssfXrJPfImu8kdH-sBXPyOl-KqmZvvT8EPw&oe=65307FD6"
                    alt="Logo"
                    class="w-[170px] h-[170px] mx-auto rounded-full object-cover mb-2 bg-gray-600 shadow-md p-2 rounded-full mx-2"
                />
            </div>

            <MainNav :hidden="hide"></MainNav>
            <div class="mt-5" :hidden="hide">
                <div class="flex flex-col text-white text-center">

                    <button
                    class="btn btn-info"
                        @click="toggleDark()"
                    >
                    <span v-if="isDark">Light Mode</span>
                    <span v-else>Dark Mode</span>
                    </button>
                </div>
            </div>
        </div>
        <div id="container" class="flex-1 p-3 dark:bg-black dark:text-white">
            <slot />

        </div>
    </div>
</template>
