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
        <div class="component">
            <label for="">搜尋課程</label>
            <input type="text" v-model="text">
            <div v-for="(item,index) in lessons" :key="index" class="list-item">
                <img :src="item.cover" alt="">
                <div>{{item.title}}</div>
            </div>
        </div>
    </div>
</template>

<script>
import practice from "../data/practice.js";

const SEARCH_API = 'https://hiskio.com/api/v1/courses/search?word=';

export default {
    data(){
        return {
            practice: practice,
            text: "",
            lessons: []
        };
    },
    methods:{
        searchLesson(value){
            fetch(`${SEARCH_API}${value}`)
            .then(function(response){
                return response.json();
            })
            .then(function(data){
                this.lessons = data.courses;
            }.bind(this));
        }
    },
    watch:{
        text(value){
            this.searchLesson(value);
        }
    }
}
</script>

<style lang="scss" scoped>
.info {
    width: 30%;
    min-height: 50vh;
    display: inline-block;
    border-right: 2px solid #11cbd7;
    padding-right: 15px;

    .title {
        font-size: 1em;
        margin: 0 auto;
        position: relative;

        &:after {
            content: "";
            position: absolute;
            left: 0;
            top: 3px;
            width: 22%;
            height: 100%;
            border-bottom: 2px solid #fa4659;
        }
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
    padding-left: 15px;
}
.list-item {
    border-top: 30px solid transparent;
    img {
        max-width: 120px;
    }
}
</style>




