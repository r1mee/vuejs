<template>    
    <section>        
        <div class="sort">
            <select v-model="sortOrder">                
                <option value="oldest">과거 목록</option>
                <!-- <option value="latest">최근 목록</option> -->
            </select>
        </div>
        <ul class="todo--list">
            <li class="todo--item" v-for="(todoItem,index) in sortedPropsdata" :key="index">
                <i class="check--icon fas fa-check" aria-hidden="true"></i>
                <div class="write--mode" v-if="editIndex !== index">
                    <p class="text">{{ todoItem.value }}</p>
                </div>
                <div class="edit--mode" v-else>
                    <input v-model="editedTodo" @keyup.enter="saveTodo(todoItem.key)" />
                </div>
                <div class="button--wrap">
                    <button 
                        type="button" 
                        class="button--edit" 
                        @click="editTodo(index)"
                    >
                        <i class="edit--icon far fa-edit" aria-hidden="true"></i>
                    </button>
                    <button 
                        type="button" 
                        class="button--remove" 
                        @click="removeTodo(index, todoItem.key)"
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
            editIndex: null,
            editedTodo: '',
            sortOrder: 'oldest',
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
        removeTodo(index_, key){
            const index = this.propsdata?.findIndex((todo) => {
                return key === todo.key;
            });
            this.$emit('removeTodo', index, key);
        },       
        editTodo(index) {
            this.editIndex = index;
            this.editedTodo = this.propsdata[index].value;
        },
        // saveTodo(index, key) {
        //     this.$emit('editTodo', index, key, this.editedTodo);
        //     this.editIndex = null;
        // },
        saveTodo(key) {
            const index = this.propsdata.findIndex((todo) => todo.key === key);
            this.$emit('editTodo', index, key, this.editedTodo);
            this.editIndex = null;
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