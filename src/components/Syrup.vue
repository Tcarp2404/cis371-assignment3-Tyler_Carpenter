<template>
  <div
    class="syrup"
    :style="{ backgroundColor: color }"
  ></div>
</template>

<script setup lang="ts">
type Props = {
  color: string;
};

defineProps<Props>();
</script>

<style lang="scss" scoped>
.syrup {
  transform: translateY(400%);
  position: relative;
  width: 100%;
  height: 20%;
  animation: pour-tea 2s 1s forwards;
  z-index: 2;
}
</style>
