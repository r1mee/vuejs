<template>
  <div class="home">
    <HeaderView />
    <ToDoInput />
    <ListView />
    <FooterView />
  </div>
</template>

<script>
// @ is an alias to /src
import HeaderView from './HeaderView.vue';
import ToDoInput from '@/components/ToDoInput.vue';
import ListView from './ListView.vue';
import FooterView from './FooterView.vue';

export default {
  name: 'HomeView',
  components: { 
    HeaderView, 
    ToDoInput,
    ListView, 
    FooterView,
  }
}
</script>

<style scoped lang="scss">
.home{
  padding:2rem;
}
</style>