<template>
  <h1 class="title">tic-tac-toe</h1>
  <Grid :gameGrid="gameGrid" @click="pressedCell" />
  <Button />
</template>

<script>
import Grid from '@/components/Grid.vue';
import Button from '@/components/Button.vue';

export default {
  name: 'app',
  components: {
    Grid,
    Button,
  },
  data() {
    return {
      gameGrid: [0, 0, 0, 0, 0, 0, 0, 0, 0],
      step: 1,
    };
  },
  methods: {
    pressedCell({ target }) {
      const isTargetClick = target.classList.contains('cell');

      if (isTargetClick) {
        const cellIndex = target.dataset.index;

        this.gameGrid[cellIndex] = this.step;

        if (this.step === 2) {
          this.step = 1;
        } else {
          this.step = 2;
        }
      }
    },
  },
};
</script>

<style lang="scss">
:root {
  --color-primary: #7F8189
  --color-secondary: #5D5F66
  --color-header: #fff
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
