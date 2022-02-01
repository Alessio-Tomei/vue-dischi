<template>
<section>
    <div class="container">
        <div class="row mb-3">
            <div class="col-12">
                <SearchBar
                @genreUp="setFilterGenre" 
                @authorUp="setFilterAuthor"
                @searchUp="setFilterAlbum"
                :disc-arr="discArray"
                />
            </div>
        </div>    
        <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-xl-5 gy-4 gx-5">
            <div class="col"  
            v-for="(disc, index) in filteredDiscArray"
            :key="index">
                <DiscBox :disc-obj="disc"/>
            </div>
        </div>
    </div>
    <LoadingWait/>
</section>
</template>

<script>
import axios from 'axios';
import DiscBox from '../commons/DiscBox.vue'
import SearchBar from '../commons/SearchBar.vue';
import LoadingWait from '../commons/LoadingWait.vue';


export default {
    name: 'DiscSection',
    components: {
        DiscBox,
        SearchBar,
        LoadingWait,
    },
    data() {
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            loading: true,
            discArray: [],
            filterAlbum: '',
            filterGenre: '',
            filterAuthor: '',

        }
    },
    methods: {
        getDiscs: function() {
            axios.get(this.apiUrl)
            .then((apiResponse) => {
                this.discArray = apiResponse.data.response
                this.loading = false;
            })
            .catch(() => {
                console.log('error');
            });
        },
        setFilterAlbum: function(inputText) {
            this.filterAlbum = inputText;
        },
        setFilterGenre: function(selecValue) {
            this.filterGenre = selecValue;
        },
        setFilterAuthor: function(selecValue) {
            this.filterAuthor = selecValue;
        },
    },
    created: function() {
        this.getDiscs();
    },
    computed: {
        filteredDiscArray() {
            return this.discArray.filter((discElement) => {
                return (
                    discElement.title.toLowerCase().includes(this.filterAlbum.toLowerCase()) &&
                    discElement.genre.toLowerCase().includes(this.filterGenre.toLowerCase()) &&
                    discElement.author.toLowerCase().includes(this.filterAuthor.toLowerCase())
                );
            });
        },  
    },
}
</script>

<style lang="scss" scoped>

</style>