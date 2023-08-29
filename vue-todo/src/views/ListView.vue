<template>    
    <section>        
        <div class="sort">
            <select v-model="sortOrder">
                <option value="latest">최근 목록</option>
                <option value="oldest">과거 목록</option>
            </select>
        </div>
        <ul class="todo--list">
            <li class="todo--item" v-for="(todoItem,index) in sortedPropsdata" :key="index">
                <i class="check--icon fas fa-check" aria-hidden="true"></i>
                <div class="write--mode">
                    <p v-if="index !== editIndex" class="text">{{ todoItem }}</p>
                    <input v-else v-model="editedTodo" class="text" @keyup.enter="saveTodo(index)" @blur="saveTodo(index)">
                </div>              
                <div class="button--wrap">
                    <button 
                        v-if="index !== editIndex" 
                        type="button" 
                        class="button--edit" 
                        @click="startEditing(index)"
                    >
                        <i class="edit--icon far fa-edit" aria-hidden="true"></i>
                    </button>
                    <button 
                        type="button" 
                        class="button--remove" 
                        @click="removeTodo(todoItem,index)"
                    >
                        <i class="remove--icon far fa-trash-alt" aria-hidden="true"></i>
                    </button>
                </div>
            </li>
        </ul>
    </section>
</template>
<script>
export default{
    props: ['propsdata'],
    data() {
        return {
            editIndex: -1,
            editedTodo: '',
            sortOrder: 'latest',
        };
    },
    computed:{
        sortedPropsdata() {
            if (this.sortOrder === 'latest') {
                return this.propsdata.slice().reverse(); // 최신순
            } else if (this.sortOrder === 'oldest') {
                return this.propsdata.slice(); // 과거순 (원래 순서 그대로)
            }

            return this.propsdata;
        }
    },
    methods:{
        removeTodo(todoItem, index){
            this.$emit('removeTodo', todoItem, index);
        },
        startEditing(index) {
            this.editIndex = index;
            this.editedTodo = this.propsdata[index];
        },
        saveTodo(index) {
            this.$emit('editTodo', index, this.editedTodo);
            this.editIndex = -1;
        },
        
    }
}
</script>
<style scoped lang="scss">
    ul{
        overflow:auto;
        max-height:224px;
        list-style-type:none;
        padding-left:0;
        margin-top:20px;
        text-align:left;
    }
    li{
        display:flex;
        min-height:50px;
        line-height:50px;
        margin:0.5rem 0;
        padding:0 0.9rem;
        background:#eee;
        border-radius:5px;;
    }
    .check--icon{
        line-height:45px;
        color:#666;
        margin-right:5px;
    }
    .button{
        &--wrap{
            margin-left:auto;
        }
        &--remove{
            margin:0 10px;
            color:#dd4343;    
        }
    }
    .sort{
        position:absolute;
        top:110px;
        right:20px;
        select {
            width:82px;
            padding:5px;
            border:1px solid #999;
        }
    }

</style>