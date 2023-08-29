<template>
  <div class="home">
    <HeaderView :todoItems="todoItems"></HeaderView>
    <ToDoInput @addTodo="addTodo"></ToDoInput>
    <ListView 
      v-bind:propsdata="todoItems" 
      @removeTodo="removeTodo" 
      @editTodo="editTodo">
    </ListView>

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
  components:{
    'HeaderView' : HeaderView, 
    'ToDoInput' : ToDoInput,
    'ListView' : ListView, 
    'FooterView' : FooterView,
  },
  data(){
    return{
      todoItems: [],

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
    },
    editTodo(index, editedTodo) {
      const currentTime = new Date().toLocaleString();
      const storedTodo = localStorage.getItem(this.todoItems[index]);

      if (storedTodo) {
        const updatedDate = `${editedTodo} (수정: ${currentTime})`;
        localStorage.setItem(updatedDate, storedTodo);
      }
      this.todoItems[index] = `${editedTodo} (수정: ${currentTime})`;
    },
  },
}
</script>

<style scoped lang="scss">
.home{
  position:relative;
  min-height:500px;
  margin:60px;
  padding:20px;
  background:#fff;
}
</style>