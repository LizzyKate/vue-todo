<template>
  <div >
     <input type="text" class="todo-input" placeholder="What needs to be done" v-model="newTodo" @keyup.enter="addTodo()">
     <div v-for="(todo, i) in todos" :key="todo.id" class="todo-item">
       <div class="todo-item-left">
       <div v-if="!todo.editing" class="todo-item-label" @dblclick="editTodo(todo)">{{todo.title.toUpperCase()}}</div>
       <input v-else class="todo-item-edit" type="text" v-model="todo.title" @blur="doneEdit(todo)" @keyup.enter="doneEdit(todo)" @keyup.esc="cancelEdit()" v-focus/>
       </div>
       <div class="remove-item" @click="removeTodo(i)">&times;</div>
     </div>
  </div>
</template>

<script>



export default {
data(){
 return{
   newTodo:'',
   idForTodo:3,
   beforeEditCache:'',
   todos:[
     {
       id:1,
       title:'Finish Vue Screencast',
       completed:false,
       editing:false
     },
     {
       id:1,
       title:'Take Over World',
       completed:false,
       editing:false
     }
   ]
 }
},
methods:{
  addTodo(){
    if(this.newTodo.trim().length === 0){
      return
    }

   this.todos.push({
     id:this.idForTodo,
     title:this.newTodo,
     completed:false,
     editing:false
   })

   this.newTodo = '',
   this.idForTodo++
  },
  removeTodo(i){
    this.todos.splice(i, 1)
  },
  
  editTodo(dow){
    dow.editing = true
  },
  doneEdit(down){
    down.editing = false
  },
  cancelEdit(odo){
 
    odo.editing = false
  }
},

directives:{
  focus:{
    inserted:function(el){
      el.focus()
    }
  }
}
 
}
</script>


<style lang="scss">
.todo-input{
  width: 100%;
  padding: 10px 18px;
  font-size: 18px;
  margin-bottom: 16px;
}
.todo-item{
  margin-bottom: 12px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.remove-item{
  cursor: pointer;
  margin-left: 14px;
}
.todo-item-left{
  display: flex;
  align-items: center;
}
.todo-item-label{
  padding: 10px;
  border:1px solid white;
  margin-left: 12px;
}
.todo-item-edit{
  color: #2c3e50;
  margin-left: 12px;
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
}
</style>