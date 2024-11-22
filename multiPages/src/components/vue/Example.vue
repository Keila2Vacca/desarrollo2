<script setup>
import Iconomas from "./Iconomas.vue";
import Iconomenos from "./Iconomenos.vue";
import {ref} from 'vue';

const name = "Keila";
const counter = ref(0);
const characters = ref([]);

console.log("Hola bitches, soy", name);

function decrement() {
    if (counter.value > 0) {
        counter.value--;
    }
}
function increment() {
    counter.value++;
    characters.value.push(counter.value);
}

</script>

<template>
    <div class="mx-auto mt-5 bg-blue-300 max-w-96 rounded-md py-4 px-6">
        <div class="flex">
            <div class="relative">
                <img class="rounded-full size-20" src="https://img.freepik.com/fotos-premium/icono-plano-aislado-fondo_1258715-220771.jpg" alt="foto de perfil">
                <div v-show="counter > 0" class="absolute top-0 right-0 flex bg-red-600 text-white size-auto rounded-full justify-center items-center">
                {{ counter }}
                </div>
            </div>

            <div class="mx-4">
                <h1 class="font-bold">
                    Hola, {{ name }}
                </h1>
                <p v-if="counter > 0" class="bg-stone-200 px-3 rounded-lg mt-2">¡Tienes {{ counter }} mensajes nuevos! </p>
                <p v-else class="bg-stone-200 px-3 rounded-lg mt-2">¡Nadie te escribe! </p>
            </div> 
        </div>
        <div class="flex justify-around w-24 mt-4">
            <button @click="decrement" class="text-white bg-blue-500 rounded px-2 size-7 flex justify-center items-center">
                <Iconomenos></Iconomenos>
            </button>
            {{ counter }}
            <button @click="increment" class="text-white bg-blue-500 rounded px-2 size-7 flex justify-center items-center">
                <Iconomas></Iconomas>
            </button>
        </div>
    </div>

    <!-- saca el valor de cada casilla del array -->
    <div v-for= "(name, index) in characters" :key="index" class="inline-block mt-3 mx-1 bg-green-400 mb-1 px-2 rounded-md max-w-max">
        {{ name }}
    </div>
</template>