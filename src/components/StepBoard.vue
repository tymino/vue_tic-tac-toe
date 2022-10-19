<template>
  <div class="step-board">
    <img
      class="step-board__icon"
      :style="currentStep !== 1 && { opacity: 0.2 }"
      src="../assets/circle.png"
      alt="circle"
      draggable="false"
    />
    <p class="step-board__text" :class="setTextClass">
      {{ setText }}
    </p>
    <img
      class="step-board__icon"
      :style="currentStep !== 2 && { opacity: 0.2 }"
      src="../assets/close.png"
      alt="close"
      draggable="false"
    />
  </div>
</template>

<script>
export default {
  name: 'c-step-board',
  props: {
    currentStep: {
      type: Number,
      default: 1,
      required: true,
    },
    isWinner: {
      type: Boolean,
      default: false,
      required: true,
    },
  },
  computed: {
    setTextClass() {
      return this.currentStep === 1
        ? 'step-board__text--player1'
        : 'step-board__text--player2';
    },
    setText() {
      return this.isWinner ? 'win' : 'turn';
    },
  },
};
</script>

<style lang="scss" scoped>
.step-board {
  display: flex;
  align-items: center;
  margin: 30px auto 0px;
  user-select: none;
}

.step-board__icon {
  width: 40px;
  height: 40px;
}

.step-board__text {
  margin: 0;
  padding: 0 20px;
  font-size: 1.8rem;
  font-weight: bold;
  text-transform: uppercase;

  &--player1 {
    color: var(--color-player1);
  }
  &--player2 {
    color: var(--color-player2);
  }
}
</style>
