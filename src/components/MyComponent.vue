<template>
  <div>This is my component {{ title }}</div>
</template>

<script>
export default {
  name: "MyComponent",
  data: () => ({
    counter: 0,
  }),
  props: ["title"],
  methods: {},
};
</script>

<style lang="scss" scoped src="../styles/components/_my-component.scss" />
