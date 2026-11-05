<template>
  <div>
    <Beverage
      :isIced="currentTemp === 'Cold'"
      :base="currentBase"
      :creamer="currentCreamer"
      :syrup="currentSyrup"
    />

    <ul>
      <!-- Temperature Selection -->
      <li>
        <h3>Temperature</h3>
        <label v-for="temp in temps" :key="temp">
          <input
            type="radio"
            name="temperature"
            :value="temp"
            v-model="currentTemp"
          />
          {{ temp }}
        </label>
      </li>

      <!-- Base Beverage Selection -->
      <li>
        <h3>Base Beverage</h3>
        <label v-for="base in bases" :key="base.id">
          <input
            type="radio"
            name="base"
            :value="base"
            v-model="currentBase"
          />
          {{ base.name }}
        </label>
      </li>

      <!-- Creamer Selection -->
      <li>
        <h3>Creamer</h3>
        <label v-for="creamer in creamers" :key="creamer.id">
          <input
            type="radio"
            name="creamer"
            :value="creamer"
            v-model="currentCreamer"
          />
          {{ creamer.name === 'No Cream' ? 'No Creamer' : creamer.name }}
        </label>
      </li>

      <!-- Syrup Selection -->
      <li>
        <h3>Syrup</h3>
        <label v-for="syrup in syrups" :key="syrup.id">
          <input
            type="radio"
            name="syrup"
            :value="syrup"
            v-model="currentSyrup"
          />
          {{ syrup.name }}
        </label>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Beverage from "./components/Beverage.vue";

import {
  temps,
  bases,
  creamers,
  syrups,
  currentTemp,
} from "./stores/beverage";

const currentBase = ref(bases.value[2]);
const currentCreamer = ref(creamers.value[0]);
const currentSyrup = ref(syrups.value[0]);
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin: 15px 0;
}

h3 {
  margin-bottom: 8px;
}

label {
  margin-right: 12px;
}
</style>
