<template>
  <div class="home">
    <h1>여기에 완료된 목록을 넣을까</h1>
    <TestView />
  </div>
</template>

<script>
// @ is an alias to /src
import TestView from './TestView.vue';

export default {
  name: 'HomeView',
  components: { TestView }
}
</script>

<style scoped lang="scss">
  .test {
    // background: blue;
  }
</style>