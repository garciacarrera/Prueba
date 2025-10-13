<script  setup lang="ts">
import type { Iprenda } from '@/models/Iprenda';
import PrendaItem from './PrendaItem.vue';

const props = defineProps<{
  listaprendas:Iprenda[]
}>()


</script>


<template>

<div class="p-4 items-center">
    <p class="text-2xl font-semibold mb-4 border-b pb-2 "> prenda de prendas</p>
    <div class="flex flex-wrap gap-1 sm:flex-col lg:fles-row w-full justify-start">
        <PrendaItem v-for="prenda in props.listaprendas" :prenda="prenda" class="lg:w-1/4 sm:w-full"/>
    </div>
</div>
</template>