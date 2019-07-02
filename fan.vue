<template>
    <div class="fan" :style="{width:width+'px',height:height+'px'}" @click.stop="isCollapse=!isCollapse">
        <div class="fan-item" v-for="(color,index) in colors[type]" :key="index" :style="{backgroundColor:color,transform:'translate(-50%,-50%) rotate('+(isCollapse ? 0 : (24+index*12-90))+'deg)'}">
        </div>
        <!-- <span class="fan-indicator"></span> -->
    </div>
</template>


<script>

const type_blue=['rgb(129, 199, 212)','rgb(51, 166, 184)','rgb(13, 86, 97)','rgb(0, 137, 167)','rgb(51, 103, 116)','rgb(30, 136, 168)',
                 'rgb(87, 124, 138)','rgb(88, 178, 220)','rgb(43, 95, 117)','rgb(58, 143, 183)','rgb(125, 185, 222)','rgb(81, 168, 221)'];
const type_pink=['rgb(220, 159, 180)','rgb(225, 107, 140)','rgb(142, 53, 74)','rgb(248, 195, 205)','rgb(244, 167, 185)','rgb(100, 54, 60)',
                'rgb(245, 150, 170)','rgb(181, 73, 91)','rgb(232, 122, 144)','rgb(208, 90, 110)','rgb(219, 77, 109)','rgb(254, 223, 225)'];
const type_map={
    blue:type_blue,
    pink:type_pink
};


export default {
    name:'fan',
    props:{
        width:{
            type:Number,
            default:250
        },
        height:{
            type:Number,
            default:170
        },
        type:{
            type:String,
            default:'pink'
        }
    },
    data(){
        return {
            colors:type_map,
            isCollapse:false
        }
    }
}
</script>

<style lang="scss">
.fan{
    // width: 250px;
    // height: 170px;
    position: relative;
    display: inline-block;
    //border: 1px solid pink;
    box-sizing: border-box;

    .fan-item{
        cursor: pointer;
        box-sizing: border-box;
        width: 10%;
        height: 80%;
        position: absolute;
        left: 50%;
        top: 50%;
        transform-origin:center 90%;
        transition: transform .5s ease;
    }

    .fan-indicator{
        position: absolute;
        background: white;
        left:50%;
        bottom: 13%;
        transform: translate(-50%,-50%);
        padding: 5px;
        border-radius: 5px;
    }
}
</style>


