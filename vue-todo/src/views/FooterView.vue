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
        position:absolute;
        bottom:30px;
        right:30px;
        width:8.5rem;
        height:50px;
        margin:50px auto 0;
        line-height:50px;
        border:1px solid #000;
        background-color:#fff;        
    }
    &--button{
        display:block;
        width:100%;
        height:100%;
        color:#e20303;
        cursor: pointer;
    }
}
</style>