<template>
  <div class="home">
    <h1>여기에 완료된 목록을 넣을까</h1>
    <HeaderView />
  </div>
</template>

<script>
// @ is an alias to /src
import HeaderView from './HeaderView.vue';

export default {
  name: 'HomeView',
  components: { HeaderView }
}
</script>

<style scoped lang="scss">
  .test {
    // background: blue;
  }
</style>