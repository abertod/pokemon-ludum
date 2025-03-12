<template>
  <!--
  <ul>
    <li>Pokemon 1</li>
    <li>Pokemon 2</li>
    <li>Pokemon 3</li>
    <li>Pokemon 4</li>
  </ul>
  -->

  <section class="flex flex-col mt-5">
    <button
      v-for="{ nomen, id } in optioness"
      :key="id"
      @click="$emit('electusOptio', id)"
      class="capitalize"
    >
      {{ nomen }}
    </button>
  </section>
</template>

<script setup lang="ts">
import type { Pokemon } from '../interfaces';

interface Props {
  optioness: Pokemon[];
}

defineProps<Props>();
defineEmits<{
  electusOptio: [id: number];
}>();
</script>

<style scoped>
@import 'tailwindcss';

button {
  @apply bg-yellow-300 shadow-md rounded-lg p-3 my-2 cursor-pointer w-40 text-center hover:bg-yellow-500 transition-all;
}
</style>
