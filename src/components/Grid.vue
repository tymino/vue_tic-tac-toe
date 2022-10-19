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
  margin: 20px auto;
  background: var(--color-cell-background);
  border: 4px solid var(--color-cell-background);
  border-radius: 10px;
  box-shadow: 2px 3px 4px var(--color-global-black);
  color: #fff;
}

@media (max-width: 450px) {
  .grid {
    width: 300px;
    height: 300px;
  }
}
@media (max-width: 320px) {
  .grid {
    width: 250px;
    height: 250px;
  }
}
</style>
