<template>
    <!-- <div>{{ tags }}</div> -->
    <!-- <div v-text="tags"></div> -->
    
    <!-- <div v-if="!tags.length">You have no any tags</div> -->

    <div v-for="(tag, index) in tags">
        {{ tag }}
        <a href="#" @click.prevent="removeTag(index)">&times;</a>
    </div>
    
    <!-- <input type="text" v-bind:value="newTag" /> -->
    <!-- <input 
        type="text" 
        :value="newTag" 
        v-on:keydown.enter="tags.push($event.target.value)" 
        v-on:keydown.tab.prevent="tags.push($event.target.value)" 
    /> -->

    <hr>
    <pre>{{ newTag }}</pre>
    <!-- <input 
        type="text" 
        :value="newTag" 
        @input="newTag = $event.target.value"
        @keydown.enter="tags.push(newTag)" 
        @keydown.tab.prevent="tags.push(newTag)" 
    /> -->
    <input 
        type="text" 
        v-model.trim="newTag"
        @keydown.enter="addNewTag" 
        @keydown.tab.prevent="addNewTag"
        @keydown.delete="removeLastTag"
    />

    <!-- <button v-on:click="tags.push(newTag)">OK</button> -->
</template>

<script>
export default {
    // Narrow Func
    data: () => ({
        tags: ["Vue", "React", "Angular"],
        newTag: 'nuxt'
    }),

    // data() {
    //     return {
    //         tags: ["Vue", "React", "Angular"]
    //     }
    // }

    methods: {
        addNewTag() {
            if (this.newTag) {
                this.tags.push(this.newTag)
                this.newTag = ""
            }
        },
        removeTag(index) {
            this.tags.splice(index, 1);
        },
        removeLastTag() {
            if (this.newTag.length === 0) {
                this.removeTag(this.tags.length - 1)
            }
        }
    }
}
</script>