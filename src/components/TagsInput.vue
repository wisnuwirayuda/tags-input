<template>
    <!-- <div>{{ tags }}</div> -->
    <!-- <div v-text="tags"></div> -->
    
    <!-- <div v-if="!tags.length">You have no any tags</div> -->

    <!-- <div v-for="tag in tags">{{ tag }}</div> -->
    
    <!-- <input type="text" v-bind:value="newTag" /> -->
    <input type="text" :value="newTag" />
</template>

<script>
export default {
    // Narrow Func
    data: () => ({
        tags: ["Vue", "React", "Angular"],
        newTag: 'nuxt'
    })

    // data() {
    //     return {
    //         tags: ["Vue", "React", "Angular"]
    //     }
    // }
}
</script>