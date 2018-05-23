<template>
    <div>
        <div class="info">
            <p class="title">實作目標</p>
            <ol class="target">
                <li v-for="(item,index) in practice[0].desc"
                    :key="index">
                    <span>{{item}}</span>
               </li>
            </ol>
        </div>
        <div class="component"></div>
    </div>
</template>

<script>
import practice from "../data/practice.js";
export default {
    data(){
        return {
            practice: practice
        };
    },

}
</script>

<style lang="scss" scoped>
.info {
    width: 30%;
    min-height: 50vh;
    display: inline-block;
    border-right: 2px solid #11cbd7;
    padding-right: 5px;

    .title {
        font-size: 1em;
        margin: 0 auto;
    }
}
.target {
    padding-left: 16px;

    li {
        margin-bottom: 15px;
        line-height: 1.3em;
    }  
}
.component {
    width: 60%;
    display: inline-block;
    vertical-align: top;
}
</style>




