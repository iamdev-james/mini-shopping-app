<template>
 <div id= 'foodItemBlock'>
  <h4 v-for= '(item, index) in foodItem' :key = "index" class= 'product'>
  <div id = 'image_container'>
  <img :src ='item.ImageUrl' height= '253' width= '228' id= 'product_image'/>
  <button class= 'addToCart'>ADD TO CART</button>
  </div>
<div id= 'product_details'>
 <span class= 'product_name'>
  {{ item.Title }}
</span>
<span>
  {{ item.OrgPrice }}
</span>
</div>
  </h4>
 </div>
</template>

<script>
import foodItem from '@/data/foodItem'
export default {
  data () {
    return {
      foodItem: foodItem
    }
  }
}
</script>

<style scoped>
#foodItemBlock {
  display: grid;
  grid-template-columns: repeat(4, 270px);
  justify-content: center;
  align-items: center;
  grid-gap: 10px;
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
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}
.addToCart {
  display: none;
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
}
#product_details {
  color: black;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
.product_name {
  font-size: 15px;
}

@media screen and (max-width: 700px) {
 #foodItemBlock {
  grid-template-columns: repeat(2, 150px);
  width: 100vw;
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
}
</style>
