<template>
  <Step />
</template>

<script>
import Step from './components/Step'

export default {
  name: 'App',
  components: {
    Step
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap');

body {
  background: #2c3e50;
  font-family: Inter, Roboto, Oxygen, Fira Sans, Helvetica Neue, sans-serif;
}
</style>
