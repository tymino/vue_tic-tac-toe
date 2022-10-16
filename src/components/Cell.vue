<template>
  <div class="cell">{{ cellValue }}</div>
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
};
</script>

<style lang="scss" scoped>
.cell {
  display: flex;
  justify-content: center;
  align-items: center;
  border: 2px solid #2c3e50;
  border-radius: 10px;
  box-shadow: 2px 3px 4px #152330;
  font-family: Helvetica;
  font-weight: bold;
  font-size: 4em;
  user-select: none;
  cursor: pointer;

  &:active {
    box-shadow: none;
  }
}
</style>
