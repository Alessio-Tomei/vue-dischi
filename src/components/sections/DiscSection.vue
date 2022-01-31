<template>
<section>
    <div class="container">
        <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-xl-5 gy-4 gx-5">
            <div class="col"  
            v-for="(disc, index) in discArray"
            :key="index">
                <DiscBox :discObj="disc"/>
            </div>
        </div>
    </div>
</section>
</template>

<script>
import axios from 'axios';
import DiscBox from '../commons/DiscBox.vue'


export default {
    name: 'DiscSection',
    components: {
        DiscBox,
    },
    data() {
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            loading: true,
            discArray: [],
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
        }
    },
    created: function() {
        this.getDiscs();
    }
}
</script>

<style lang="scss" scoped>

</style>