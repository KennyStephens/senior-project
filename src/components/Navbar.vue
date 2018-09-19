<template>
  <div>
    <ul>
      <li v-for="navItem in navItems" :key="navItem">{{ navItem }}</li>
    </ul>
    
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      navItems: ['Home', 'About Us', 'Sign In']
    }
  }
}
</script>

<style lang="scss" scoped>
  ul {
    float: right;
    padding: 20px 5px 0 0;
    margin-bottom: 0;
    
    li {
      float:left;
      width: 100px;
      list-style-type: none;
      color: #fff;
      text-align: center;
      cursor: pointer;

      &:hover {
        color: aqua;
      }
    }

  }
</style>

