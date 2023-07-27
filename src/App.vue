<script setup>
import { computed, ref } from 'vue';

  const name = "Fidel";
  const styleColor = "color: blue";
  const activo = false;
  const objColores = [{
    name: "rojo",
    description: "Rojo",
    stock: 0
  },
  {
    name: "azul",
    description: "Azul",
    stock: 1
  },
  {
    name: "verde",
    description: "Verde",
    stock: 2
  }];
  const objColor = {
    name: "amarillo",
    description: "Amarillo",
  }

  const handleClick = (message) => {
    console.log(message);
  }

  const counter = ref(0);

  const increment = () => {
    counter.value++;
  }

  const decrement = () => {
    counter.value--;
  }

  const reset = () => {
    counter.value = 0;
  }

  const classCounter = computed(() => {
    if (counter.value === 0) {
      return 'zero';
    } if (counter.value > 0) {
      return 'positive';
    } else {
      return 'negative';
    }
  })
</script>

<template>
  <h1 :style="styleColor">Hola {{name.toUpperCase()}}</h1>
  <h2 v-if="activo">Estoy activo</h2>
  <h2 v-else>Estoy inactivo</h2>
  
  <ul>
    <!-- <li v-for="(item, index) in arrayColores" :key="index">
      {{ item }}
    </li> -->
    <li v-for="item in objColores" :key="item.name">
      {{ item.name }} - {{ item.description }}
    </li>
    <li v-for="(value, propiedad) in objColor" :key="value">
      {{ propiedad }} : {{ value }}
    </li>
    <template v-for="item in objColores" :key="item.name">
      <li v-if="item.stock > 0">
        {{ item.name }} - {{ item.description }}
      </li>
    </template>
  </ul>

  <button v-on:click="handleClick('Texto 1')">Activar 1</button>
  <button @click="handleClick('Texto 2')">Activar 2</button>

  <button @click="increment()">Aumentar</button>
  <button @click="decrement()">Disminuir</button>
  <button @click="reset()">Reiniciar</button>
  <!-- <h2 :class="counter > 0 ? 'positive' : 'negative' ">{{ counter }}</h2> -->
  <h2 :class="classCounter">{{ counter }}</h2>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  color: red;
}

.positive {
  color: greenyellow;
}

.negative {
  color: red;
}

.zero {
  color: black;
}
</style>
