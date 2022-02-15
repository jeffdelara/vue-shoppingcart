<template>
  <div class="base-component">
    Sample Component Initialization, <br />
    omit this file if you started working on your project 🤞

    <div>Clicks: {{ counter }}</div>

    <button v-on:click="addCount">Click Me</button>
  </div>
</template>

<script>
export default {
  name: "BaseComponent",
  data: () => ({
    counter: 0,
  }),
  methods: {
    addCount() {
      this.counter += 1;
    },
  },
};
</script>

<style lang="scss" scoped src="../styles/components/_base-component.scss" />
