<template>
  <div class="container">
    <div class="header">
      <h1>TODO LIST</h1>
    </div>
    <todo-input @addTodo="addTodoItem" class="todo"></todo-input>
    <todo-list :todoItem="todoItem" @reDel="removeDel" class="todo"></todo-list>
    <todo-footer @clearAll="clearAll" class="todo"></todo-footer>
  </div>
</template>

<script>
import TodoFooter from './components/TodoFooter.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
export default {
  components: {
     TodoInput,
     TodoList,
     TodoFooter,
    },
  data(){
    return{
      todoItem:[]
    }
  },
  created(){
    for(let i=0;i<localStorage.length;i++){
      this.todoItem.push(localStorage.key(i))
    }
  },
  methods:{
    addTodoItem(item){
    this.todoItem.push(item);
    localStorage.setItem(item,item)
    },
    removeDel(num,item){
      this.todoItem.splice(num,1)
      localStorage.removeItem(item)
    },
    clearAll(){
      localStorage.clear();
      this.todoItem = [];
    }

  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR&display=swap');
  @import url('./assets/reset.css');
  body,html{
    font-family: 'Noto Sans KR', sans-serif;
    height: 100%;
  }
  body{
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .container{
    width: 700px;
    background: honeydew;
    border: 2px solid #666;
    border-radius: 20px;
    padding: 20px;
  }

  .todo{
    margin-bottom: 30px;
  }
    
    

</style>