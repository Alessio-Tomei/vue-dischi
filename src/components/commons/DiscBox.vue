<template>
<div class="ms_disc-box">
    <div class="ms_scale-1-2">
        <div>
            <div class="ms_scale-1-1">
                <img :src="discObj.poster" alt="">
            </div>
            <h4>{{discObj.title}}</h4>
            <p>{{discObj.author}}</p>
            <p>{{discObj.year}}</p>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'DiscBox',
    props: {
        discObj: Object,
    },
}
</script>

<style lang="scss" scoped>
@import "../../assets/style/variables.scss";

.ms_disc-box {
    width: 100%;
    background-color: $bg-light-color;
    .ms_scale-1-2 {
        width: 100%;
        padding-top: 182%;
        position: relative;
        top: 0;
        left: 0;
    }
    .ms_scale-1-2 > div{
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        left: 0;
        padding: 20px;
        display: flex;
        flex-direction: column;
        align-items: center;
        .ms_scale-1-1 {
            width: 100%;
            padding-top: 100%;
            position: relative;
            top: 0;
            left: 0;
            img {
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
            }
        }
        h4 {
            margin-top: 10%;
            margin-bottom: 10%;
            max-height: 24%;
            overflow-y: auto;
            text-overflow: ellipsis;
            text-align: center;
            text-transform: uppercase;
            word-break: break-word;
            &::-webkit-scrollbar {
                display: none;
            }
        }
        p {
            color: $color-belittle;
            margin: 0px;
            width: 100%;
            text-align: center;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            &:first-of-type {
                margin-bottom: 5%;
            }
        }
    }
}
</style>