<template>
  <header>
    <h1>TODO TODO</h1>
    <p class="total">목록 총 개수 : {{ totalTodoItems }} </p>
  </header>
</template>

<script>
export default {
    name: 'HeaderView',
    props: ['todoItems'], 
    computed: {
      totalTodoItems() {
        return this.todoItems.length;
      },
    }
}
</script>

<style scoped lang="scss">
h1{
    color:#2f3b52;
    font-size:30px;
    font-weight:800;
    margin:30px auto;
}
.total{
  display:flex;
  justify-content: flex-start;
  margin:20px auto 0;
}
</style>