<script setup lang="ts">
import { ref } from 'vue';
import type { Iprenda } from '@/models/Iprenda';
import ListaPrendas from './ListaPrendas.vue';

const prendasIniciales: Iprenda[] = [
  { id: 1, nombre: 'Camisa Clásica', talle: 'M', color: 'Azul', precio: 50.99, stock: 12 },
  { id: 2, nombre: 'Pantalón Cargo', talle: 'L', color: 'Verde', precio: 89.50, stock: 4 },
  { id: 3, nombre: 'Vestido Veraniego', talle: 'S', color: 'Rojo', precio: 35.00, stock: 0 },
  { id: 4, nombre: 'Chaqueta Denim', talle: 'XL', color: 'Azul', precio: 120.00, stock: 15 },
  { id: 5, nombre: 'Jersey de Lana', talle: 'M', color: 'Gris', precio: 65.75, stock: 6 },
  { id: 6, nombre: 'Short Deportivo', talle: 'S', color: 'Negro', precio: 25.00, stock: 2 },
  { id: 7, nombre: 'Falda Plisada', talle: 'L', color: 'Negro', precio: 45.00, stock: 0 },
];





const prendas = ref<Iprenda[]>([...prendasIniciales]);


const talleSeleccionado = ref<string>('todos');

// Corrige el método de ordenar, hace sort y actualiza el array reactivo
const ordenar = (): void => {
  prendas.value = [...prendas.value].sort((a, b) => a.precio - b.precio);
};

const filtros = (): void => {
  let resultadofiltrado = [...prendasIniciales];
  const talle = talleSeleccionado.value;
  if (talle !== 'todos') {
    resultadofiltrado = resultadofiltrado.filter(p => p.talle === talle);
  }
  prendas.value = resultadofiltrado;
};

const resetFiltros = (): void => {
  talleSeleccionado.value = 'todos';
  prendas.value = [...prendasIniciales];
};
</script>

<template>
  <div class="py-2 px-1 w-full">
    <h1 class="text-3xl font-bold mb-4">CatalogoManager</h1>
    <div class="mb-8 p-4 bg-amber-50 rounded-sm">
      <h2 class="text-xl font-semibold">Controles</h2>
      <div class="flex flex-wrap gap-6 mb-2">
        <div>
          <label for="talle-select" class="block font-medium mb-1">Talle:</label>
          <select
            class="p-2 border rounded-sm"
            name="talle-select"
            id="talle-select"
            v-model="talleSeleccionado"
            @change="filtros"
          >
            <option value="todos">Todos</option>
            <option value="S">S</option>
            <option value="M">M</option>
            <option value="L">L</option>
            <option value="XL">XL</option>
          </select>  
        </div>
      </div>
    </div>
    <div class="flex flex-wrap gap-6 mb-2">
      <button @click="ordenar">Ordenar por precio</button>
      <button @click="resetFiltros">Reset</button>
    </div>
    <ListaPrendas :listaprendas="prendas"/>
  </div>
</template>