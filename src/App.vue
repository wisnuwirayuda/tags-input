<script>
export default {
  data: () => ({
    jsFrameworks: ["React.js", "Vue.js", "Angular"]
  })
}
// import TagsInput from './components/TagsInput.vue';
// export default {
//   components: { TagsInput }
// }
</script>

<template>
  <h1>Hello World</h1>
  <tags-input :selectedTags="jsFrameworks"></tags-input>
  <!-- <tags-input /> -->
  <!-- <TagsInput /> -->
</template>

<style>
h1 {
  color: blue;
}
</style>
