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
            this.todoItems.push({key: i, value: localStorage.getItem(i)});
        }
    }
  },
  methods:{
    addTodo(todoItem){
      const key = this.todoItems.length;
      localStorage.setItem(key, todoItem);
      this.todoItems = [...this.todoItems, {key, value:todoItem}];
    },
    removeTodo(index, key){
      console.log(key, localStorage.getItem(key))
      localStorage.removeItem(key);
      this.todoItems.splice(index,1);
    },
    clearTodo(){
      localStorage.clear();
      this.todoItems = [];
    },
    editTodo(index, key, newTodo) {
      try {
        // const currentTime = new Date().toLocaleString();
        const storedTodo = localStorage.getItem(key);

        if (!storedTodo) {
          throw new Error('존재하지 않는 Todo를 수정하려합니다')
        }

        // {key: value {content: ''updateDate: '',createDate: '',}}
        const updatedDate = newTodo;

        const newTodoItems = [...this.todoItems];
        newTodoItems[index] = {...newTodoItems[index], value:updatedDate}

        this.todoItems = newTodoItems;
        localStorage.setItem(key, updatedDate);
      } catch (error) {
        //...
      }
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