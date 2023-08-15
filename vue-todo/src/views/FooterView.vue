<template>
    <div class="clear--wrap">
        <button type="button" class="clear--button" @click="clearTodo">전체 삭제</button>
    </div>
</template>
<script>
export default{
    methods:{
        clearTodo(){
            this.$emit('clearTodo');
        }
    }
}
</script>
<style scoped lang="scss">
.clear{
    &--wrap{
        width:8.5rem;
        height:50px;
        line-height:50px;
        background-color:#fff;
        border-radius:5px;
        margin:0 auto;
    }
    &--button{
        display:block;
        width:100%;
        height:100%;
        margin:20px auto 0;
        color:#e20303;
        cursor: pointer;
    }
}
</style>