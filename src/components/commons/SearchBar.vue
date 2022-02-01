<template>
<div class="search-bar">
    <input 
    type="text" 
    placeholder="Cerca un album..."
    v-model.trim="inputText"
    @keyup="$emit('searchUp', inputText)"
    >
    <div>
        <label for="genre">Genere: </label>
        <select name="" id="genre" v-model="genreValue" @change="$emit('genreUp', genreValue)">
            <option value="">All</option>
            <option :value="genre" v-for="(genre, index) in optionsGenre" :key="index">{{genre}}</option>
        </select>
    </div>
    <div>
        <label for="authors">Autori: </label>
        <select name="" id="authors" v-model="authorValue" @change="$emit('authorUp', authorValue)">
            <option value="">All</option>
            <option :value="author" v-for="(author, index) in optionsAuthor" :key="index">{{author}}</option>
        </select>
    </div>
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
    display: flex;
    background-color: $bg-light-color;
    padding: 20px;
    input {
        width: 40%;
        padding: 0px 20px;
        border-radius: 5px;
        border: none;
        outline: none;
    }
     & > div {
        width: 30%;
        padding-left: 20px;
        display: flex;
        justify-content: flex-end;
    }
    label {
        width: 60px;
        text-align: end;
        margin-right: 10px;
    }
    select {
        width: calc(100% - 60px);
        max-width: 200px;
        padding: 0px 5px;
        border-radius: 5px;
        cursor: pointer;
    }
}

</style>