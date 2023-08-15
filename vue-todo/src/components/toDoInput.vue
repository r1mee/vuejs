<template>
    <div class="input--box shadow">
        <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
        <button type="button" class="button--add" v-on:click="addTodo">
            <span class="blind">추가</span>
            <i class="button--icon fas fa-plus" aria-hidden="true"></i>
        </button>
    </div>
</template>

<script>
export default {
    name: 'ToDoInput',
    data(){
        return{
            newTodoItem: '',
        }
    },
    methods:{
        addTodo(){
            if(this.newTodoItem !== ""){
                var value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.clearInput();
            }
            
        },
        clearInput(){
            this.newTodoItem = '';
        }
    }
}
</script>

<style scoped lang="scss">
input{
    display:inline-block;
    padding:0 4rem 0 1rem;
    box-sizing:border-box;
    border-radius:5px;
}
.input{
    &--box{
        position:relative;
        background:#fff;
        height:50px;
        line-height:50px;
    }

}
.button{
    &--add{
        position:absolute;
        top:0;
        right:0;
        background:linear-gradient(to right, #6478fb, #8763fb);
        width:3rem;
        height:100%;
        border:0;
        border-radius:0 5px 5px 0;
    }
    &--icon{
        color:#fff;
        vertical-align:middle;
    }
}
</style>