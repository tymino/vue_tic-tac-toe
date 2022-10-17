<template>
  <button class="button">{{ buttonName }}</button>
</template>

<script>
export default {
  name: 'c-button',
  props: {
    buttonName: {
      type: String,
      default: 'click',
    },
  },
};
</script>

<style lang="scss" scoped>
.button {
  align-self: center;
  padding: 10px 20px;

  background: var(--color-cell-background);
  border: 1px solid var(--color-cell-background);
  border-radius: 6px;
  box-shadow: 1px 2px 3px var(--color-global-black);

  color: var(--color-player2);
  font-size: 1.2rem;
  font-weight: bold;
  text-transform: uppercase;

  transition: border ease 0.4s;
  user-select: none;
  cursor: pointer;

  &:hover {
    border: 1px solid var(--color-player1);
  }

  &:active {
    box-shadow: 1px 2px 2px inset var(--color-global-black);
    padding-top: 11px;
  }
}
</style>
