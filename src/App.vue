<template>
    <div id="app">
      <TodoHeader></TodoHeader>
      <div id="box">
        <TodoInput v-on:addTodo="addTodo"></TodoInput>
        <TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList>
      </div>
      <TodoFooter v-on:removeAll="clearTodo"></TodoFooter>
    </div>
</template>

<script>
import TodoHeader from './components/TodoHeader';
import TodoInput from './components/TodoInput';
import TodoList from './components/TodoList';
import TodoFooter from './components/TodoFooter';

export default {
  data() {
    return {
      todoItems: []
    };
  },
  created() {
        if(localStorage.length > 0){
            for(var i = 0 ; i < localStorage.length; i++){
              if(localStorage.key(i) != "loglevel:webpack-dev-server"){
                this.todoItems.push(localStorage.key(i));
              }
            }
        }
  },
  methods:{
    addTodo(todoItem){
      localStorage.setItem(todoItem,todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodo(todoItem, index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index,1);
    },
    clearTodo(){
      localStorage.clear();
      this.todoItems = [];
    }
  },
    components: {
      'TodoHeader': TodoHeader,
      'TodoInput': TodoInput,
      'TodoList': TodoList,
      'TodoFooter': TodoFooter
    }
}
</script>

<style>
#box{
  width:500px;
  margin: 0px auto;
  margin-top: 10px;
  padding : 15px;
  text-align:center;
  border: 1px solid gray; 
}
</style>