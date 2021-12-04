<template>
 <Header id = 'header'/>
    <div class="bg_normal" :class = 'currentClass' id="main">
    <section id="nav-bar">
      <div class="PD-10">
        <i class="color_whitePD far fa-dot-circle fa-2x MT15"></i>
      </div>
      <div class="icon_blue flex_column">
        <i class="fab fa-facebook M10"></i>
        <i class="fab fa-instagram M10"></i>
        <i class="fab fa-wpressr M10"></i>
      </div>
    </section>
    <section id="page-body">
      <div id="header_nav" class="flex_row MT20">
        <div>
          <ul>
            <li class="MRL15"><router-link to='/'>Home</router-link></li>
            <li class="MRL15">About</li>
            <li class="MRL15"><router-link to = '/product/shop'>Market place</router-link></li>
            <li class="pop MRL15">Blog</li>
            <li class="pop MRL15">Contact Us</li>
          </ul>
        </div>
        <div>
         <router-link to='/product/shop'>
          <i class="fas fa-shopping-cart"></i>
         </router-link>
        </div>
      </div>
      <div id="content-section" class="MT30 PB20">
        <div class="part_a">
          <img :src="require('@/assets/skate.png')" alt="skate-pic" id = 'showcaseImg'>
          <h1 class="part_a_word1">SPEEDY</h1>
          <h1 class="part_a_word2">QUADS</h1>
        </div>
        <div class="part_b">
          <div id="part_b_header" class="flex_row_nospace">
           <h2 class="h2_header"><i> PONNKN </i> SPEEDY QUADS </h2>
           <span class="stars ML35 color_orange">
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
            <i class="fas fa-star"></i>
           </span>
          </div>
          <small>Lorem ipsum dolor sit.</small>
          <h2>$ 500.</h2>
          <p class="MT20">Lorem ipsum dolor sit amet consectetur adipisicing elit. Laborum mollitia at autem neque dicta nemo nam eaque amet enim iusto a incidunt recusandae delectus illum harum veritatis itaque consequuntur, reprehenderit doloribus consequatur ex molestias et! Molestias odio officiis numquam, commodi voluptatum qui nisi quasi, eligendi, consequatur perferendis deleniti quaerat enim.</p>
          <a href="#">Neirnfier</a>
          <div>
            LIBET:
            <span @click = 'setCurrentColor("blue")' id="blue_container" class="SHW"> </span>
            <span @click = 'setCurrentColor("pink")' id="pink_container" class="SHW"> </span>
            <span @click = 'setCurrentColor("yellow")' id="yellow_container" class="SHW"> </span>
            <span @click = 'setCurrentColor("grey")' id="grey_container" class="SHW"> </span>
          </div>
          <div>
            PA3MEP:
            <select id="select_shit">
            <option>Extension</option>
            <option>Lorem.</option>
            <option>Lorem, ipsum.</option>
            <option>Ajiehdee</option>
            </select>
          </div>
          <button id="part_b_btn"> Edhtrugytgb a eufbruf </button>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Header from '@/components/header.vue'
export default {
  el: '#main',
  components: {
    Header
  },
  data () {
    return {
      currentColor: '',
      currentClass: ''
    }
  },
  methods: {
    changeBgColor (color) {
      if (color === 'pink') {
        this.currentClass = 'pinkyClass'
      } else if (color === 'grey') {
        this.currentClass = 'greyClass'
      } else if (color === 'yellow') {
        this.currentClass = 'yellowClass'
      } else if (color === 'blue') {
        this.currentClass = 'blueClass'
      }
    },
    setCurrentColor (colorName) {
      this.currentColor = colorName
      this.changeBgColor(this.currentColor)
    }
  }
}
</script>

<style scoped>
#main {
  height: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
}
.bg_normal {
  background: linear-gradient(40deg, #1ac3f7, #06bdf5, #059cca, #0392bf);
  height: 100%;
}
/* UTILITY CLASS */
#header {
  display: none;
}
h1 {
  font-size: 42px;
}
.M10 {
  margin: 10px auto;
}
.MRL15 {
  margin: auto 15px;
}
.MT15 {
  margin-top: 15px;
}
.MT20 {
  margin-top: 20px;
}
.MT30 {
  margin-top: 5rem;
}
.ML35 {
  margin-left: 35px;
}
.PB20 {
  padding-bottom: 20px;
}
.color_orange {
  color: rgb(255, 231, 93);
  font-size: 11px;
}
.textwidth {
  width: 120px;
}
a {
  color: whitesmoke;
  text-decoration: none;
  font-size: 19px;
}
#showcaseImg {
  width : 250px;
  height : 300px;
}
.SHW {
  padding: 3px 11px;
  border: 1px solid whitesmoke;
  border-radius: 50px;
  margin-left: 10px;
}
.color_whitePD {
  color: white;
  padding: 10px;
  background: rgb(230, 108, 129);
  border-radius: 50%;
}
.icon_blue {
  color: #2090b3d8;
}
/* COLOR PANEL */
#blue_container {
  background: #0392bf;
}
#pink_container {
  background: #ed48ba;
}
#yellow_container {
  background: #fbec06;
}
#grey_container {
  background: #b3d4e0;
}
#nav-bar {
  height: 100vh;
  width: 14%;
  background-color: #afdbe7d8;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}
#page-body {
  height: 100vh;
  color: whitesmoke;
  display: flex;
  flex-direction: column;
}
.flex_row {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
.flex_row_nospace {
  display: flex;
  flex-direction: row;
  align-items: center;
}
.flex_column {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
ul {
  list-style: none;
  display: flex;
  flex-direction: row;
  font-size: 19px;
}
#content-section {
  height: 65%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
.part_a {
 height: 100%;
 flex: 1;
 display: flex;
 flex-direction: column;
 justify-content: center;
 align-items: center;
 position: relative;
}
.part_a_word1, .part_a_word2 {
  position: absolute;
  color: aliceblue;
  text-shadow: 1px 2px 1px black;
  font-weight: 800;
  line-height: 40px;
}
.part_a_word1{
  left: 8rem;
  bottom: 46px;
}
.part_a_word2 {
  left: 12rem;
  bottom: 12px;
}
.part_b {
  height: auto;
  padding-right: 5rem;
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;
}
.h2_header {
  font-size: 30px;
}
#select_shit {
  height: 35px;
  width: 150px;
  outline: none;
  background: transparent;
  border: 1px solid whitesmoke;
}
#part_b_btn {
  height: 38px;
  width: 200px;
  text-align: center;
  background: #dd50b0;
  border: none;
  color: white;
}
/* COLOR CLASSES */
.pinkyClass {
  background: linear-gradient(35deg, #fd93dc, #fa76d0, #ed48ba,#fd1db6);
}
.greyClass {
  background: linear-gradient(35deg, #7e97a0, #b3d4e0, #a0ddf3, #92dffc) ;
}
.yellowClass {
  background: linear-gradient(40deg, #fced20, #fbec06, #dbcd04, #867e05);
}
.blueClass {
  background: linear-gradient(40deg, #1ac3f7, #06bdf5, #059cca, #0392bf);;
}

@media (max-width: 800px) {
  #main {
    height: 100%;
  }
  .MRL15 {
    margin: auto 10px;
  }
  .part_b {
    padding-left: 3rem;
    /* justify-content: center;
    align-items: center; */
  }
  ul {
   display: none;
  }
  #header {
   display: block;
  }
  #content-section {
    height: 100%;
    flex-direction: column;
    justify-content: space-around;
  }
  .h2_header {
    margin-top: 15px;
  }
  .stars {
    display: none;
  }
}
@media (max-width: 500px) {
  #nav-bar {
    display: none;
  }
  div ul {
    flex-direction: column;
  }
 ul li .pop {
    display: none !important;
  }
}
@media (max-width: 350px) {
  .MRL15 {
    margin: auto 5px;
  }
}
</style>
