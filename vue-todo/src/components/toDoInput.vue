<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
        <div>
            <button type="button" class="addButton" v-on:click="addTodo">
                추가
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ToDoInput',
    data: function() {
        return {
            newTodoItem: ""
        }
    },
    methods:{
        addTodo: function(){
            console.log(this.newTodoItem);
            localStorage.setItem(this.newTodoItem, this.newTodoItem);
            this.clearInput();
        },
        clearInput:function(){
            this.newTodoItem="";
        }
    }
}
</script>
<style scoped>
input:focus {
    outline: none;
}
.inputBox {
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
    outline: 1px solid black;
}
.inputBox input {
    border-style: none;
    font-size: 0.9rem;
}
.addButton {
    float: right;
    background: #3d3d3d;
    width: 3rem;
    color:#fff;
    border-radius: 0 5px 5px 0;
}
</style>