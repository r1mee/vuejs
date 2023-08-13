<template>
  <div class="home">
    <TestView />
    <ToDoInput />
  </div>
</template>

<script>
// @ is an alias to /src
import TestView from './TestView.vue';
import ToDoInput from '@/components/ToDoInput.vue';

export default {
  name: 'HomeView',
  components: { TestView, ToDoInput }
}
</script>

<style scoped lang="scss">
.home {
  background:red;
}
</style>