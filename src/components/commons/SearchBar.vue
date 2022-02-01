<template>
<div class="search-bar">
    <input 
    type="text" 
    placeholder="Cerca un album..."
    v-model.trim="inputText"
    @keyup="$emit('searchUp', inputText)"
    >
    <select name="" id="" v-model="genreValue" @change="$emit('genreUp', genreValue)">
        <option value="">All</option>
        <option :value="genre" v-for="(genre, index) in optionsGenre" :key="index">{{genre}}</option>
    </select>
    <select name="" id="" v-model="authorValue" @change="$emit('authorUp', authorValue)">
        <option value="">All</option>
        <option :value="author" v-for="(author, index) in optionsAuthor" :key="index">{{author}}</option>
    </select>
</div>
</template>

<script>
export default {
    name: 'SearchBar',
    props: {
        discArr: Array,
    },
    data() {
        return {
            inputText: '',
            optionsGenre: [],
            optionsAuthor: [],
            genreValue: '',
            authorValue: '',
        }
    },
    methods: {
        generateOption: function() {
            this.discArr.forEach((discItem) => {
                if (!this.optionsGenre.includes(discItem.genre)) {
                    this.optionsGenre.push(discItem.genre);
                }
                if (!this.optionsAuthor.includes(discItem.author)) {
                    this.optionsAuthor.push(discItem.author);
                }
            });
        }
    },
    watch: {
        discArr: function() {
            this.generateOption();
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../../assets/style/variables.scss";

.search-bar {
    background-color: $bg-light-color;
    padding: 50px;
    input {
        width: 30%;
        padding: 0px 20px;
        border-radius: 5px;
        border: none;
        outline: none;
    }
}

</style>