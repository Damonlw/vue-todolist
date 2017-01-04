<template>
  <div class="todo-list">
    <h1 v-text="title"></h1>
    <label for="">{{ some }}</label>
    <input type="text" v-model="newItem" @keyup.enter="addItem" placeholder="input">
    <ul>
        <li v-for=" (item, index) in items"
            :class="[{finished:item.finished},'li-style',{unfinished:item.unfinished}]"
            @click="toggle(item)"
        >
            {{item.text}}
            <div class="del-btn" @click.stop="del(index)">X</div>
        </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'todo-list',
  data () {
    return {
        some:'Plz:',
        title:'Welcome to here!',
        newItem:'',
        items:[
            {
                text:'未完成',
                finished:false,
                unfinished:true
            },
            {
                text:'未完成',
                finished:false,
                unfinished:true
            },
            {
                text:'未完成',
                finished:false,
                unfinished:true
            }
        ]
    }
    },
    methods:{
        addItem:function(){
            if(this.newItem=='完成'){
                this.items.push({
                    text:this.newItem,
                    finished:true,
                    unfinished:false
                });
            }else{
                this.items.push({
                    text:this.newItem,
                    finished:false,
                    unfinished:true
                });
            }
            this.newItem=''
        },
        toggle:function(item){
            item.finished=!item.finished;
            item.unfinished=!item.unfinished;
            if(item.text=='未完成'){
                item.text='完成';
            }else if(item.text=='完成'){
                item.text='未完成';
            }
        },
        del:function(index){
            console.log(index);
            this.items.splice(index,1)
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .finished{
        background:#42b983;
    }
    .unfinished{
        background: rgba(255, 102, 102, 1);
    }
    .li-style{
        width: 200px;
        margin:0 0 1px 49%;
        transform: translateX(-49%);
        cursor: pointer;
        border-radius: 3px;
        position: relative;
    }
    .del-btn{
        width: 18px;
        height: 18px;
        color: #fff;
        font-size: 14px;
        position: absolute;
        right: 5px;
        top: 2px;
        z-index: 10;
        cursor: pointer;
    }
</style>
