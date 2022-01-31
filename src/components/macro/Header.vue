<template>
<header>
    <div class="container-fluid">
        <div class="row">
            <div class="col">
                <div class="ms_img-container">
                    <img src="https://storage.googleapis.com/pr-newsroom-wp/1/2018/11/Spotify_Logo_RGB_Green.png" alt="">
                </div>
            </div>
        </div>
    </div>
</header>
</template>

<script>
export default {
    name: 'Header',
}
</script>

<style lang="scss" scoped>
@import "../../assets/style/variables";

header {
    background-color: $bg-light-color;
}

.ms_img-container {
    width: 61px;
    overflow: hidden;
    img {
        width: 200px;
        padding: 10px 0px;
    }
}
</style>