<template>
    <!-- <div>{{ tags }}</div> -->
    <!-- <div v-text="tags"></div> -->
    
    <!-- <div v-if="!tags.length">You have no any tags</div> -->

    <div v-for="tag in tags">{{ tag }}</div>
    
    <!-- <input type="text" v-bind:value="newTag" /> -->
    <!-- <input 
        type="text" 
        :value="newTag" 
        v-on:keydown.enter="tags.push($event.target.value)" 
        v-on:keydown.tab.prevent="tags.push($event.target.value)" 
    /> -->
    <input 
        type="text" 
        :value="newTag" 
        @keydown.enter="tags.push($event.target.value)" 
        @keydown.tab.prevent="tags.push($event.target.value)" 
    />

    <!-- <button v-on:click="tags.push(newTag)">OK</button> -->
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