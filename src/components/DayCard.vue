<script setup lang="ts">
import type { IWeekDay } from '@/models/IWeekDay';



const props= defineProps<{
    dias:IWeekDay
}>();



</script>


<template>


    <div :class="{'bg-red-500': props.dias.selected===true}" class="max-w-xs mx-auto p-4 rounded-lg border shadow-sm">
  
  <h3 class="text-lg font-semibold text-gray-800 mb-1">
    {{ props.dias.name }}
  </h3>
  
  <p class="text-sm text-gray-600 mb-3">

  </p>
  
  
  
</div>
</template>