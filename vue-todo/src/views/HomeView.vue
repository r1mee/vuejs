<template>
  <div class="home">
    <HeaderView />
    <ToDoInput />
  </div>
</template>

<script>
// @ is an alias to /src
import HeaderView from './HeaderView.vue';
import ToDoInput from '@/components/ToDoInput.vue';

export default {
  name: 'HomeView',
  components: { HeaderView, ToDoInput }
}
</script>

<style scoped lang="scss">
.home{
  padding:2rem;
}
</style>