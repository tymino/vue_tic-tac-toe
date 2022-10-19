<template>
  <div class="cell" ref="cell">
    <img
      v-if="cellValue == 1"
      class="cell_icon"
      src="../assets/circle.png"
      alt="circle"
      draggable="false"
    />
    <img
      v-else-if="cellValue == 2"
      class="cell_icon"
      src="../assets/close.png"
      alt="close"
      draggable="false"
    />
  </div>
</template>

<script>
export default {
  name: 'c-cell',
  props: {
    cellValue: {
      type: Number,
      default: 0,
    },
  },
  watch: {
    cellValue() {
      const refCellBlock = this.$refs.cell.classList;

      if (this.cellValue === 0) {
        refCellBlock.remove('active');
      }
      if (this.cellValue > 0) {
        refCellBlock.add('active');
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.cell {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 2px;

  border: 2px solid var(--color-grid-background);
  border-radius: 10px;
  box-shadow: 2px 3px 4px var(--color-global-black);

  font-family: Helvetica;
  font-weight: bold;
  font-size: 4em;

  user-select: none;
  cursor: pointer;

  &.active {
    box-shadow: 1px 2px 3px inset var(--color-global-black);
    border: 2px solid var(--color-cell-background);
    cursor: default;
  }
}

.cell_icon {
  width: 70%;
  height: auto;
}
</style>
