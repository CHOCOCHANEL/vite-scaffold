<template>
  <div>
    <button v-on:click="increment">Counter: {{ counter }}</button>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        counter: 0,
      }
    },
    methods: {
      increment() {
        this.counter++;
      },
    },
    mounted() {
      console.log('A component has been mounted');
    },
  }
</script>

<style lang="scss" scoped>

</style>