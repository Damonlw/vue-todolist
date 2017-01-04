<template>
  <div id="app">
    <img src="./assets/logo.png" @click="display" :class="'img-cursor'">
    <div class="tab-main" v-show="showTab">
        <div
            v-for="(item, index) in items"
            :class="['tab', {checked:item.isChecked}]"
            @click="change(item.modalName,item)"
        >
            {{item.value}}
        </div>
    </div>
    <component :is="modal"></component>
  </div>
</template>

<script>
import todoList from './components/todoList'
import todo from './components/todo'
import Hello from './components/Hello'
import areaSelect from './components/areaSelect'

export default {
  name: 'app',
  data(){
     return{
         showTab:false,
         items: [
             {value: 'First', modalName: 'Hello',isChecked:false},
             {value: 'Second', modalName: 'areaSelect',isChecked:false},
             {value: 'Last', modalName: 'todoList',isChecked:false}
         ],
         modal: null
     }
  },
  methods:{
    display:function(){
      this.showTab=!this.showTab
    },
    change:function(string,item){
        this.modal = string !== this.modal ? string : null;
        this.items.map((item) => {
             item.modalName === string&&this.modal!==null ? item.isChecked = true : item.isChecked = false })
    }
  },
  components: {
      Hello:Hello,
      todo:todo,
      todoList:todoList,
      areaSelect:areaSelect
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.tab-main{
    width:227px;
    height: 31px;
    margin-left: 50%;
    transform: translateX(-50%);
    clear: both;
}
.tab-main .tab{
    width: 70px;
    height: 30px;
    line-height: 30px;
    border: 1px solid #ccc;
    border-radius: 3px;
    float: left;
    cursor: pointer;
}
.checked{
    color: #fff;
    border-color: rgba(91, 192,222, 1);
    background: rgba(91, 192,222, 1);
}
.img-cursor{
    cursor: pointer;
}
</style>




<!-- for(let i=0;i<this.items.length;i++){
   if(this.items[i].modalName===string&&this.modal!==null){
       this.items[i].isChecked = true
   }else{
       this.items[i].isChecked = false
   }
} -->
