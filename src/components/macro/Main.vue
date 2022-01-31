<template>
<main>
    <DiscSection/>
</main>
</template>

<script>
import DiscSection from '../sections/DiscSection.vue';
export default {
    name: 'Main', 
    components: { 
        DiscSection,
    },
}
</script>

<style lang="scss" scoped>

main {
    padding: 50px 0px;
}

</style>