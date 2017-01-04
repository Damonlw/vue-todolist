<template>
<div class="todo">
    <div class="all">
        <div class="form-group">
            <label for="">Name:</label>
            <input type="text" v-model="newPerson.name">
        </div>
        <div class="form-group">
            <label for="">&nbsp;&nbsp;&nbsp;Age:</label>
            <input type="text" v-model="newPerson.age">
        </div>
        <div class="form-group">
            <label for="">&nbsp;&nbsp;&nbsp;&nbsp;Sex:</label>
            <select v-model="newPerson.sex">
                <option value="Male">Male</option>
                <option value="Female">Female</option>
            </select>
        </div>
        <div class="form-group">
            <button class="btn create-btn" type="button" @click="create">Creat</button>
        </div>
    </div>
    <table>
        <thead>
            <tr class="tr-th">
                <th>Name</th>
                <th>Age</th>
                <th>Sex</th>
                <th>Delete</th>
            </tr>
        </thead>
        <tbody>
            <tr class="tr-td" v-for="(person,index) in people">
                <td>{{ person.name}}</td>
                <td>{{ person.age}}</td>
                <td>{{ person.sex}}</td>
                <td>
                    <button class="btn" type="button" @click="del(index)">Delete</button>
                </td>
            </tr>
        </tbody>
    </table>
</div>
</template>

<script>
export default {
  name: 'todo',
  data () {
    return {
        newPerson: {
                      name: '',
                      age: '',
                      sex: 'Male'
                  },
          people: [{
              name: 'Jack',
              age: 30,
              sex: 'Male'
          }, {
              name: 'Bill',
              age: 26,
              sex: 'Male'
          }, {
              name: 'Tracy',
              age: 22,
              sex: 'Female'
          }, {
              name: 'Chris',
              age: 36,
              sex: 'Male'
          }],
    }
},
    methods:{
        create:function(){
            this.people.push(this.newPerson);
            this.newPerson={name:'',age:'',sex:'Male'}
        },
        del:function(index){
            this.people.splice(index,1)
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .all{
        width: 200px;
        margin: 0 auto;
    }
    .form-group{
        width: 200px;
        text-align: left;
        margin-bottom: 3px;
    }
    .btn{
        color: #fff;
        background:#42b983;
        border: 1px solid #42b983;
        border-radius: 4px;
        cursor: pointer;
    }
    .create-btn{
        margin-left: 52px;
    }
    table{
        width: 70%;
        border-collapse:collapse;
        margin: 7px 0 0 15%;
        border-top: 1px solid #ccc;
        border-left: 1px solid #ccc;
        border-right: 1px solid #ccc;
    }
    .tr-th{
        background:#42b983;
    }
    .tr-td{
        border-bottom: 1px solid #ccc;
    }
    .tr-td td{
        border-right: 1px solid #ccc;
    }
    .todo{
        width: 734px;
        margin: 27px auto;
    }
    /*@media screen and (min-width: 1450px) {
        .filed-style {
            margin-right: 13%;
            transform: translateX(-95%);
        }
    }*/
</style>
