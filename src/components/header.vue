<template>
  <div id= 'container'>
    <nav id= 'nav-bar'>
     <router-link to="/"><i class="fas fa-crown ML-50"></i></router-link>
     <p @click = 'showCart()' class= 'cart MR-50'><i class="fas fa-shopping-bag"></i></p>
    </nav>
  </div>
  <i></i>
</template>
<script>
export default {
  name: '#App',
  data () {
    return {
      status: false
    }
  },
  methods: {
    showCart () {
      this.$emit('cartStatus', true)
    }
  }
}
</script>
<style scoped>
  #container {
    position: sticky;
    top: 0;
    width: 100vw;
    height: auto;
    z-index: 5;
    background: white;
    box-shadow: 1px 1px 2px black;
  }
  #nav-bar {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    padding: 16px 20px;
    align-items: center;
    font-size: 21px;
    margin-bottom: 15px;
    color: black;
  }
  a {
    text-decoration: none;
    color: black;
  }
  .cart {
    cursor: pointer;
  }
  .ML-50 {
    margin-left: 50px;
    opacity: 0.7;
  }
  .MR-50 {
    margin-right: 50px;
    opacity: 0.7;
  }
</style>
