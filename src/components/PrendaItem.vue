<script  setup lang="ts">
import  type { Iprenda } from '@/models/Iprenda';


const props = defineProps<{
  prenda:Iprenda
}>()


const GetColoresStock =(stock: number ):string => {
  if (stock===0) {
    return 'border-red-500 bg-red-50 text-red-800' // Stock is 0
   }else if(stock<=5){ // Stock is 1, 2, 3, 4, or 5
    return 'border-yellow-500 bg-yellow-50 text-yellow-800' // Green (Good/Medium)
   }else{ // Stock is > 5 (i.e., 6, 7, 8, ...)
    return 'border-green-500 bg-green-50 text-green-800' // Green (Good/High)
   }
}



</script>


<template>
  

<div class="p-2 m-2 border-b-2 rounded-sm" :class="GetColoresStock(props.prenda.stock)">
  <h3> {{ props.prenda.nombre }}</h3>
  <p>precio: {{ props.prenda.precio }}</p>
  <p>color: {{ props.prenda.color }}</p>
  <p>Stock: {{ props.prenda.stock }}</p>

</div>
  
</template>
