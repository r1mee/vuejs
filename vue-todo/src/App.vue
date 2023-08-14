<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link> | 
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/>
  </div>
</template>
<script>

</script>
<style lang="scss">
@import '@/assets/styles/global.scss';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
    text-align:center;
    background-color:#f6f6f8;
}

.shadow{
    box-shadow: 5px 10px 10px rgba(0,0,0,.3);
}
input{
  width:100%;
  height:100%;
  border-style: none;
  font-size:0.9rem;
  
  &:focus{
      outline: none;
  }
}
.blind{
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
button{
  padding:0;
  border:0;
  background:none;
}
nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
