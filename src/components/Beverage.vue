<template>
  <Mug>
    <Cold v-if="isIced" />
    <Hot v-else />

    <Contents>
      <!-- Top layer: Creamer when syrup is also selected -->
      <template v-slot:top>
        <Creamer
          v-if="creamer.name !== 'No Cream' && syrup.name !== 'No Syrup'"
          :color="creamer.color"
        />
      </template>

      <!-- Middle layer: Syrup, or creamer when there is no syrup -->
      <template v-slot:mid>
        <Syrup
          v-if="syrup.name !== 'No Syrup'"
          :color="syrup.color"
        />

        <Creamer
          v-else-if="creamer.name !== 'No Cream'"
          :color="creamer.color"
        />
      </template>

      <!-- Bottom layer: Always show the selected base -->
      <template v-slot:bottom>
        <Base :color="base.color" />
      </template>
    </Contents>
  </Mug>
</template>

<script setup lang="ts">
import Contents from "./Contents.vue";
import Mug from "./Mug.vue";
import Syrup from "./Syrup.vue";
import Base from "./Base.vue";
import Creamer from "./Creamer.vue";
import Hot from "./Hot.vue";
import Cold from "./Cold.vue";

type Ingredient = {
  id: string;
  name: string;
  color: string;
};

type Props = {
  isIced: boolean;
  base: Ingredient;
  creamer: Ingredient;
  syrup: Ingredient;
};

defineProps<Props>();
</script>
