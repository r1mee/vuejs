<template>
  <div class="home">
    <HeaderView></HeaderView>
    <ToDoInput @addTodo="addTodo"></ToDoInput>
    <ListView v-bind:propsdata="todoItems" @removeTodo="removeTodo"></ListView>
    <FooterView @clearTodo="clearTodo"></FooterView>
  </div>
</template>

<script>
// @ is an alias to /src
import HeaderView from './HeaderView.vue';
import ToDoInput from '@/components/ToDoInput.vue';
import ListView from './ListView.vue';
import FooterView from './FooterView.vue';

export default{
  name: 'HomeView',
  data(){
    return{
      todoItems: []
    }
  },
  created(){
    if(localStorage.length > 0){
        for(var i = 0 ; i < localStorage.length; i++){
            this.todoItems.push(localStorage.key(i));
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
  components:{
    'HeaderView' : HeaderView, 
    'ToDoInput' : ToDoInput,
    'ListView' : ListView, 
    'FooterView' : FooterView,
  }
}
</script>

<style scoped lang="scss">
.home{
  padding:2rem;
}
</style>