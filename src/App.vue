<script>
export default {
  data: () => ({
    jsFrameworks: ["React.js", "Vue.js", "Angular"],
    otherFrameworks: []
  }),
  methods: {
    handleChange(tags) {
      this.jsFrameworks = [...tags];
    }
  }
}
// import TagsInput from './components/TagsInput.vue';
// export default {
//   components: { TagsInput }
// }
</script>

<template>
  <h1>Hello World</h1>
  <p>{{ jsFrameworks }}</p>
  <tags-input :selectedTags="jsFrameworks" @change="handleChange"></tags-input>
  <!-- <tags-input /> -->
  <!-- <TagsInput /> -->

  <p>{{ otherFrameworks }}</p>
  <tags-input :selectedTags="otherFrameworks" @change="otherFrameworks = [...$event]"></tags-input>
</template>

<style>
h1 {
  color: blue;
}
</style>
