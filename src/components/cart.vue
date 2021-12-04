<template>
  <div>
  <Header />
    <table id= 'itemTable'>
      <tr id= 'table_header'>
        <th> Product </th>
        <th> Description </th>
        <th> Quantity </th>
        <th> Price </th>
        <th> Remove </th>
      </tr>
      <tr v-for = '(cart, index) in cart' :key= 'index'>
        <img :src= 'cart.imgUrl' id = 'itemImg' />
        <td v-text="cart.itemname"></td>
        <td><input id= 'count'  :value="cart.count" disabled/></td>
        <td> {{ cart.totalprice.toFixed(2) }}</td>
        <td><i @click = 'removeItem(cart.id)' class="fas fa-trash"></i></td>
      </tr>
    </table>
    <hr />
     <h2 id= 'total'> TOTAL: N {{ total.toFixed(2) }}</h2>
  </div>
  <div id= 'payoutSec'>
    <p class= 'textDanger'>*Please use the following test credit card for payment*</p>
    <p class= 'textDanger'>4242 4242 4242 4242- Exp: 01/20- CW: 123</p>
    <button id= 'payNow'>Pay Now</button>
  </div>
</template>
<script>
import Header from '@/components/header.vue'
export default {
  props: {
    cart: Array,
    total: Number
  },
  components: {
    Header
  },
  data () {
    return {
      index: Number
    }
  },
  methods: {
    removeItem (idToRemove) {
      this.cart.forEach(product => {
        if (product.id === idToRemove) {
          this.index = this.cart.indexOf(product)
          this.$emit('removeItem', this.index)
        }
      })
    }
  }
}
</script>
<style scoped>
 #itemTable {
 margin: auto;
 }
 td {
  text-align: center;
 }
 #itemImg {
   height : 70px;
   width : 70px;
   padding: 20px 10px;
 }
 th {
  border-bottom: 1px solid #333;
  padding: 20px 35px;
 }
 td {
  padding: 20px 35px;
 }
 #count {
  text-align: center;
  width: 50px;
  height: 30px;
  border: 1px solid skyblue;
  border-radius: 10px;
  outline: none;
 }
 #total {
  text-align: right;
  margin-right: 280px;
  margin-top: 30px;
  font-weight: 300px;
 }
 #payoutSec {
  margin: auto;
  margin-top: 60px;
 }
 .textDanger {
  color: red;
  font-size: 18px;
 }
 #payNow {
  padding: 10px 30px;
  outline: none;
  border: none;
  color: white;
  background: blue;
  box-shadow: 1px 1px 2px black;
  border-radius: 10px;
  margin-right: -15rem;
  margin-top: 30px;
 }
</style>
