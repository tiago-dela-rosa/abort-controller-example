<script setup lang="ts">
import { ref } from 'vue'
import axios from "axios";

interface IPokemon {
  name: number;
  url: string;
}

const controller = ref<AbortController>();
const isLoading = ref(false)
const pokemons = ref<IPokemon[]>([])
const genSelected = ref(0)

const ourService = async (gen = 1, signal: any) => { 
  const genOne = '?limit=150'
  const genTwo = '?limit=100&offset=151'
  const range = gen > 1 ? genTwo : genOne;  
  try {
    const { data } = await axios.get(`https://pokeapi.co/api/v2/pokemon/${range}`, { signal });
    return data.results;
  } catch (e) {
  }
}

const getPokemonsByGen = async (genenation: number) => {
  isLoading.value = true
  genSelected.value = genenation
  controller.value?.abort();
  controller.value = new AbortController();
  
  pokemons.value = await ourService(genSelected.value, controller.value.signal);
  isLoading.value = pokemons.value.length === 0;
}
</script>

<template>
  <section>
    <h1>What is your favorite generation?</h1>
    <div>
      <button :class="{active: genSelected === 1 }" @click="getPokemonsByGen(1)">Gen One</button>
      <button :class="{active: genSelected === 2 }" @click="getPokemonsByGen(2)">Gen Two</button>
    </div>
    <h2 v-if="isLoading">Loading...</h2>
    <ul v-else>
      <li v-for="mon in pokemons" :key="mon.name">
        <img width="30" :src="`https://img.pokemondb.net/artwork/${mon.name}.jpg`" />
        {{ mon.name }}
      </li>
    </ul>
  </section>
</template>
