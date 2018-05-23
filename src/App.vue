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
    	<div class="content">
       		<component :is="currentView"></component>
    	</div>
  	</div>
</template>

<script>
import practice from "./data/practice.js";
import SearchLesson from "./component/SearchLesson.vue";
import TicTocToe from "./component/TicTocToe.vue";

export default {
  	name: "app",
  	data() {
    	return {
      		currentView: "SearchLesson",
      		isActive: 0
    	};
  	},
  	components: {
    	SearchLesson,
    	TicTocToe
  	},
  	computed: {
    	practice() {
      		return practice;
    	}
  	},
  	methods: {
    	selectItem(index, component) {
      		this.isActive = index;
      		this.currentView = component;
    	}
  	}
};
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
		background-color: #f0fff3;
		color: #11cbd7;
		// border-bottom: 1px solid #11cbd7;
		margin-bottom: 10px;
		font-weight: 600;
  	}
  	span {
    	display: inline-block;
    	padding: 3px 5px;
    	min-height: 20px;
    	cursor: pointer;
    	border: 1px solid #11cbd7;
		// border-top-width: 0px;
		color: #11cbd7;
    	font-size: 1em;
		// margin-right: 5px;
		// margin-left: 5px;
  	}
  	span.active {
    	color: #fff;
    	background-color: #11cbd7;
  	}
}
.content {
  	padding: 15px 20px;
}
</style>
