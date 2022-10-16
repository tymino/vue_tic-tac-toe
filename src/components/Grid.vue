<template>
  <div class="grid">
    <cell
      v-for="(cell, index) in gameGrid"
      :key="index"
      :cellValue="cell"
      :data-index="index"
    />
  </div>
</template>

<script>
import Cell from '@/components/Cell.vue';

export default {
  name: 'c-grid',
  components: {
    Cell,
  },
  props: {
    gameGrid: {
      type: Array,
      default: () => [],
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
.grid {
  display: grid;
  grid-template: repeat(3, 1fr) / repeat(3, 1fr);
  width: 400px;
  height: 400px;
  margin: 0 auto;
  background: #415e7c;
  border: 6px solid #364d64;
  border-radius: 10px;
  color: #fff;
}
</style>
