<template>
  <div id="app">
    <div class="practice-list">
      <div class="tag">課後練習</div>
      <span v-for="(item,index) in practice" 
            :key="index"
            :class="{active:isActive===index}"
            @click="selectItem(index , item.component)">
        {{item.title}}
      </span>
    </div>
    <hr>
    <div class="content">
      <component :is="currentView"></component>
    </div>
  </div>
</template>

<script>
import practice from './data/practice.js'
import SearchLesson from './component/SearchLesson.vue';
import TicTocToe from './component/TicTocToe.vue';

export default {
  name: 'app',
  data () {
    return {
      currentView: 'SearchLesson',
      isActive: 0,
    }
  },
  components:{
    SearchLesson,
    TicTocToe
  },
  computed:{
    practice(){
      return practice;
    }
  },
  methods:{
    selectItem(index,component){
      this.isActive = index;
      this.currentView = component;
    }
  }
}
</script>

<style lang="scss">
#app {
  max-width: 50%;
  margin: 0 auto;
}
.practice-list {
  padding: 15px;
  .tag {
    padding: 5px;
  }
  span {
    display: inline-block;
    padding: 3px 5px;
    min-height: 20px;
    cursor: pointer;
    border: 1px solid #f5f5f5;
    font-size: 1em;
  }
  span.active {
    color: blueviolet;
    background-color: aliceblue;
  }
}
.content {
  padding: 15px 20px;
}


</style>
