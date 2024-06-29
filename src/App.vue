<script setup lang="ts">
import { type Ref, ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue';

const numbers: Ref<number[]> = ref([4, 3, 2, 1]);

const agregar = () => {
  const currenValue = numbers.value;
  currenValue.unshift(currenValue.length + 1);
  numbers.value = currenValue;
};

const eliminar = () => {
  const currenValue = numbers.value;
  currenValue.shift();
  numbers.value = currenValue;
};
</script>

<template>
  <HelloWorld />
  <div>
    <button @click="agregar">Agregar</button>
    <button @click="eliminar">Eliminar</button>
  </div>
  <TransitionGroup name="list" tag="ul" class="container">
    <li v-for="number in numbers" :key="number" class="item">{{ number }}</li>
  </TransitionGroup>
</template>

<style scoped>
.container {
  position: relative;
  list-style-type: none;
}

.item {
  padding: 0;
  width: 100%;
}

.list-move,
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

.list-leave-to,
.list-enter-from {
  opacity: 0;
  transform: translateX(30px);
}

.list-leave-active {
  position: absolute;
}
</style>
