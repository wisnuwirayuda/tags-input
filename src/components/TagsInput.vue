<template>
    <div class="tags-input-wrapper">
        <!-- <div>{{ tags }}</div> -->
        <!-- <div v-text="tags"></div> -->
        
        <!-- <div v-if="!tags.length">You have no any tags</div> -->

        <span class="tag-item" v-for="(tag, index) in tags" :key="index">
            {{ tag }}
            <a class="remove-tag" href="#" @click.prevent="removeTag(index)">&times;</a>
        </span>
        
        <!-- <input type="text" v-bind:value="newTag" /> -->
        <!-- <input 
            type="text" 
            :value="newTag" 
            v-on:keydown.enter="tags.push($event.target.value)" 
            v-on:keydown.tab.prevent="tags.push($event.target.value)" 
        /> -->

        <!-- <hr>
        <pre>{{ newTag }}</pre> -->
        <!-- <input 
            type="text" 
            :value="newTag" 
            @input="newTag = $event.target.value"
            @keydown.enter="tags.push(newTag)" 
            @keydown.tab.prevent="tags.push(newTag)" 
        /> -->

        <!-- <input 
            type="text" 
            v-model.trim="newTag"
            @keydown.enter="addNewTag" 
            @keydown.tab.prevent="addNewTag"
            @keydown.delete="removeLastTag"
            :class="tags.includes(newTag) ? 'tag-exists' : ''"
        /> -->

        <input 
            class="tag-input"
            type="text" 
            v-model.trim="newTag"
            @keydown.enter="addNewTag" 
            @keydown.tab.prevent="addNewTag"
            @keydown.delete="removeLastTag"
            :class="{ 'tag-exists': isTagExists }"
        />
        
        <!-- <button v-on:click="tags.push(newTag)">OK</button> -->
    </div>
</template>

<script>
export default {
    props: {
        selectedTags: {
            type: Array,
            default: () => []
        }
    },

    // Narrow Func
    data() {
        return {
            tags: [...this.selectedTags],
            newTag: ''
        }
    },

    // data() {
    //     return {
    //         tags: ["Vue", "React", "Angular"]
    //     }
    // }

    computed: {
        isTagExists() {
            return this.tags.includes(this.newTag);
        }
    },

    watch: {
        newTag (newVal) {
            if (newVal.indexOf(",") > -1) {
                this.newTag = newVal.slice(0, -1);
                this.addNewTag();
            }
        }
    },

    methods: {
        addNewTag() {
            if (this.newTag && !this.isTagExists) {
                this.tags.push(this.newTag);
                this.newTag = "";
                this.$emit('change', this.tags);
            }
        },
        removeTag(index) {
            this.tags.splice(index, 1);
            this.$emit('change', this.tags);
        },
        removeLastTag() {
            if (this.newTag.length === 0) {
                this.removeTag(this.tags.length - 1)
            }
        }
    },

    emits: ['change']
}
</script>

<style scoped>
.tag-input.tag-exists {
    color: red;
    text-decoration: line-through;
}

.tags-input-wrapper {
    background: #fff;
    padding: 0.5em;
    border: 1px solid #dbdbdb;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    min-height: 36px;
    box-sizing: border-box;
}

.tag-item {
    color: #212529;
    background-color: #eee;
    margin-right: 0.3em;
    padding: 0.25em 0.4em;
    font-size: 75%;
    line-height: 1;
    text-align: center;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    padding-right: 1.25em;
    padding-left: 0.6em;
}

.tag-input {
    color: #495057;
    flex: 1;
    background: transparent;
    border: none;
}

.tag-input:focus {
    outline: none;
}

a.remove-tag {
    text-decoration: none;
}
</style>