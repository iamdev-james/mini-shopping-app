<template>
<Header  @cartStatus = 'toggleCartStatus($event)' />
 <div id = 'productBlock'>
  <h4 v-for= '(product, index) in product' :key = "index" class= 'product'>
  <div id= 'image_container' @mouseover = 'showBtn = index' @mouseleave = 'showBtn = -1'>
  <img :src ='product.imgUrl' id= 'product_image'/>
  <button v-show = 'showBtn === index' class= 'addToCart' @click = 'addToCart(product.name, product.imgUrl, product.price, product.id)'> ADD TO CART</button>
  </div>
  <div id= 'product_details'>
  <span class= 'product_name'>
     {{ product.name }}
  </span>
  <span>
  $: {{ product.price }}
  </span>
  </div>
  </h4>
</div>
<div v-if = 'showCart' id= 'cart_section'>
   <p @click = 'closeCart ()'><i class="far fa-times-circle fa-2x MT-20"></i></p>
   <Cart :total= 'total' :cart = 'cart' @removeItem = 'removeProduct($event)'/>
</div>
<div id= 'foodItemHeader'>
  <h1> Food Item</h1>
</div>
<div>
  <FoodItem />
</div>
</template>

<script>
import product from '@/data/product'
import FoodItem from '@/components/foodItem.vue'
import Header from '@/components/header.vue'
import Cart from '@/components/cart.vue'
export default {
  components: {
    FoodItem, Header, Cart
  },
  data () {
    return {
      product: product,
      showBtn: '',
      cart: [],
      showCart: false,
      total: 0,
      knowStat: 0
    }
  },
  methods: {
    addToCart (name, imageUrl, price, id) {
      const productObj = {
        itemname: name,
        imageUrl,
        itemprice: price,
        id: id,
        count: 1,
        totalprice: price
      }
      if (this.cart.length === 0) {
        this.cart.push(productObj)
        this.total = productObj.price
      } else if (this.cart.length >= 1) {
        var found = false
        this.cart.forEach(product => {
          if (product.id === id) {
            found = true
            product.count++
            product.totalprice = product.itemprice * product.count
            this.knowStat++
          }
        })
        if (!found) {
          this.cart.push(productObj)
          this.knowStat++
        }
        // for (const item of this.cart) {
        //   if (item.itemname === name) {
        //     if (item.id === id) {
        //       console.log(id)
        //       item.count++
        //     }
        //   } else if (item.itemname !== productObj.itemname) {
        //     this.cart.push(productObj)
        //   }
        // }
      }
    },
    toggleCartStatus (emittedStatus) {
      this.showCart = emittedStatus
    },
    removeProduct (emittedNumber) {
      this.cart.splice(emittedNumber, 1)
      this.knowStat--
    },
    closeCart () {
      this.showCart = false
    }
  },
  watch: {
    knowStat () {
      if (this.cart.length >= 1) {
        this.total = this.cart.reduce((a, b) => a + b.totalprice, 0)
      }
    }
  }
}
</script>

<style scoped>
#productBlock {
  display: grid;
  grid-template-columns: repeat(4, 270px);
  justify-content: center;
  align-items: center;
  grid-gap: 10px;
  overflow-x: hidden;
 }
.product {
  padding: 10px 30px;
  color: white;
  height: 300px;
}
#image_container {
  position: relative;
  height: 255px;
  width: 230px;
  border: 1px solid black;
}
#product_image {
  position: absolute;
  height: 253px;
  width: 228px;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}
#image_container:hover {
  opacity: 0.85;
}
.addToCart {
  width: 12rem;
  position: absolute;
  bottom: 50px;
  left: 8%;
  padding: 12px 10px;
  border: none;
  font-size: 17px;
  font-weight: 550;
  background: whitesmoke;
  color: black;
}
.addToCart:hover {
  background: black;
  color: whitesmoke;
  opacity: 1;
}
#product_details {
  color: black;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
#cart_section {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: 100%;
  overflow-x: hidden;
  background: whitesmoke;
  z-index: 6;
}
.product_name {
  font-size: 15px;
}
#foodItemHeader {
  padding: 40px 110px;
  text-align: left;
}
.MT-20 {
  margin-top: 20px;
}
@media screen and (max-width: 700px) {
 #productBlock {
  grid-template-columns: repeat(2, 150px);
 }
 .product {
  height: 150px;
 }
 #image_container {
  width: 100px;
  height: 90px;
 }
 #product_image {
  width: 98px;
  height: 80px;
 }
.addToCart {
  width: 4rem;
  bottom: 10px;
  left: 15%;
  padding: 5px 4px;
  font-size: 14px;
}
#product_details {
  flex-direction: column;
}
}
</style>
