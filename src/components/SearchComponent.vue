<template>
  <div class="base-component">
    <input
      id="search"
      autocomplete="off"
      placeholder="Search for games..."
      type="text"
      v-model="search"
    />

    <div v-if="search">
      <h2>Searching for '{{ search }}'</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchComponent",
  props: ["games"],
  data: () => ({
    search: "",
  }),

  watch: {
    search: function (val) {
      this.games.forEach((game) => {
        const title = game.title.toLowerCase();
        const searchString = val.toLowerCase();
        if (!title.includes(searchString)) {
          game.visible = false;
        } else {
          game.visible = true;
        }
      });
      console.log(this.games);
    },
  },

  methods: {},
};
</script>

<style lang="scss" scoped src="../styles/components/_search-component.scss" />
