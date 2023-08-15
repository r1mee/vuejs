<template>
    <section>
        <ul class="todo--list">
            <li class="todo--item" v-for="(todoItem,index) in propsdata" :key="todoItem">
                <i class="check--icon fas fa-check" aria-hidden="true"></i>
                <p class="text">{{ todoItem }}</p>
                <button type="button" class="button--remove" @click="removeTodo(todoItem, index)">
                    <i class="remove--icon far fa-trash-alt" aria-hidden="true"></i>
                </button>
            </li>
        </ul>
    </section>
</template>
<script>
export default{
    props: ['propsdata'],
    methods:{
        removeTodo(todoItem, index){
            this.$emit('removeTodo', todoItem, index);
        }
        
    }
}
</script>
<style scoped lang="scss">
    ul{
        list-style-type:none;
        padding-left:0;
        margin-top:0;
        text-align:left;
    }
    li{
        display:flex;
        min-height:50px;
        line-height:50px;
        margin:0.5rem 0;
        padding:0 0.9rem;
        background:#fff;
        border-radius:5px;;
    }
    .check--icon{
        line-height:45px;
        color:#666;
        margin-right:5px;
    }
    .button--remove{
        margin-left:auto;
        color:#dd4343;
    }
</style>