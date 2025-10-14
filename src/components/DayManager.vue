<script setup lang="ts">
import type { IWeekDay } from '@/models/IWeekDay';
import DayCard from './DayCard.vue';
import  {ref, toValue}  from 'vue';
import type { forEachChild } from 'typescript';




const diassemana:IWeekDay[]=[
    {id:1, name:'lunes', selected:false},
    {id:2, name:'martes', selected:false},
    {id:3, name:'miercoles', selected:false},
    {id:4, name:'jueves', selected:false},
    {id:5, name:'vienes', selected:false},
    {id:6, name:'sabado', selected:false},
    {id:7, name:'domingo', selected:false}

]

const diasseleccionado=ref<(IWeekDay[])>(diassemana)

const marcardias =(id:number)=>{

for () {
   
    
}
 
}
</script>


<template>

    <button class="w-full py-1.5 bg-green-500 text-white text-sm font-medium rounded-md hover:bg-green-600" v-for="l in diasseleccionado"   :class="marcardias(l.id)">{{ l.name }}</button>

<DayCard v-for="diasseleccionado in diassemana" :dias="diasseleccionado"/>
</template>