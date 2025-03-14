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
      :disabled="nonEligere"
      v-for="{ nomen, id } in optioness"
      :key="id"
      @click="$emit('electusOptio', id)"
      :class="[
        'capitalize disabled: shadow-none disabled:bg-gray-100',
        {
          recte: id === recteResponsio && nonEligere,
          'non-recte': id !== recteResponsio && nonEligere,
        },
      ]"
    >
      {{ nomen }}
    </button>
  </section>
</template>

<script setup lang="ts">
import { type Pokemon } from '../interfaces';

interface Props {
  optioness: Pokemon[];
  nonEligere: boolean;
  recteResponsio: number;
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

.recte {
  @apply bg-green-500 text-white;
  /* background-color: green;
  color: white;
  */
}

.non-recte {
  @apply bg-red-500 opacity-70;
  /*background-color: red;
  color: white;
  opacity: 70%;*/
}
</style>
