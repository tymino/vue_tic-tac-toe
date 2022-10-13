<template>
  <h1 class="title">tic-tac-toe</h1>
  <Grid />
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
      gameGrid: [0, 0, 0, 0, 0, 0, 0, 0],
    };
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
