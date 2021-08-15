<template>
  <nav class="container-horizontal box">
    <i @click="toggleNav" class="fa fa-bars"></i>
    <figure>
      <img
        :src="imagePathText"
        :style="{width: '13rem'}"
        ref="logo"
        class="image-visible"
        alt="logo tediber" />
    </figure>
    <ul class="container-horizontal list-in-nav" ref="nav">
<!-- Il y a 3 conditions d'affichage des elements de la navbar:
  1. une image,
  2. un texte,
  3. un texte avec un sous-menu
  ça depend des données du api json-server/navbar
  -->
      <li :key="navElem.id" v-for="navElem in navElems">
        <div
          v-if="navElem.title.includes('https')"
          :navElem="navElem">
          <img
            :src="navElem.title"
            :style="{width: '10rem'}"
            alt="logo tediber"/>
        </div>
        <!-- Hover effet sur le texte de la navbar -->
        <div
          @mouseenter="$event.currentTarget.style.color = '#999'"
          @mouseleave="$event.currentTarget.style.color = 'inherit'"
          v-else-if="navElem.content !== null"
        >
        <!-- Création du sous-menu avec v-for car le navElem.content est un tableau -->
          {{navElem.title.toUpperCase()}}<i class="fas fa-chevron-down"
            @click="toggleSubMenu"
          ></i>
          <div
            ref="products" class="sub-menu sub">
              <span
                :key="index" v-for="(sub, index) in navElem.content"
                >{{sub}}
              </span>
            </div>
        </div>
        <div
          @mouseenter="$event.currentTarget.style.color = '#999'"
          @mouseleave="$event.currentTarget.style.color = 'inherit'"
          v-else
        >
          {{navElem.title.toUpperCase()}}
        </div>
      </li>
    </ul>
    <figure>
      <img
        :src="imagePathShoppingCart"
        :style="{width: '6rem'}"
        class="image-visible"
        alt="panier d'achats"
      />
    </figure>
  </nav>
</template>
<script>
export default {
  name: 'Navbar',
  props: {
    navElems: Array,
    imagePathText: String,
    imagePathShoppingCart: String,
  },
  methods: {
		toggleNav () {
      /*
      rajouter ou supprimer la class qui fait apparaitre ou disparaitre les navbar et logo-texte
      ces class sont utilisées dans le mediaqueries
      */
			const nav = this.$refs.nav.classList
      const logo = this.$refs.logo.classList
			nav.contains('list-in-nav') ? nav.remove('list-in-nav') : nav.add('list-in-nav')
      nav.contains('container-vertical') ? nav.remove('container-vertical') : nav.add('container-vertical')
      logo.contains('image-hidden') ? logo.remove('image-hidden') : logo.add('image-hidden')
      logo.contains('image-visible') ? logo.remove('image-visible') : logo.add('image-visible')
    },
    // toggle sous-menu
    toggleSubMenu(){
      const products = this.$refs.products.classList
      products.contains('sub-menu') ? products.remove('sub-menu') : products.add('sub-menu')
    }
	}
}
</script>

<style scoped>
nav{
  position: fixed;
  top: 0;
  z-index: 1;
  width: 100%;
  height: 15vh;
}
.image-visible{
  display: inline-block;
}
.image-hidden{
  visibility: hidden;
}
span{
  display: block;
  margin: 1rem 0;
}
.sub{
  position: absolute;
  margin: 1rem 0;
  background-color: #fff;
  width: 9vw;
}
.sub-menu{
  display: none;

  /* height: 10vh; */
}
.container-horizontal img{
  display: inline-block;
}
.container-vertical img{
  display: none;
}
ul li{
  list-style: none;
  font-size: 1.4rem;
  font-weight: 700;
  letter-spacing: 1.5px;
  color: var(--tedicolor);
  cursor: pointer;
}
a{
  text-decoration: none;
  color: inherit;
}
/* le menu bourger */
.fa-bars{
  display: none;
}
@media (orientation: landscape) and (min-width : 300px){
  nav{
    height: 27vh;
  }
}
@media screen and (max-width: 1199px) {
  .fa-bars{
    position: absolute;
    display: block;
    left: 10px;
    top: 7px;
    color: var(--tedicolor);
    font-size: 3.5rem;
    padding: .5rem;
    z-index: 99;
  }
  .fa-bars:hover{
    transition: transform 3s;
    transform: rotate(180deg);
  }
  nav{
    justify-content: space-evenly;
  }
  figure:first-of-type{
    position: absolute;
    width: 100%;
    z-index: 11;
    text-align: center;
    margin: .5rem auto;
  }
  figure:last-of-type img{
    position: absolute;
    top: 0;
    right: 0;
    margin: .5rem;
  }
  .list-in-nav{
    display: none;
  }
  ul{
    position: absolute;
    top: 6rem;
    left: 0;
    width: 100vw;
    height: 30vh;
    z-index: 2;
    flex-direction: column;
    align-items: flex-start;
    border-bottom: 1px solid var(--lightgrey);
    box-shadow: 1px 2.5px 2px 2.5px var(--verylightgrey);
    background-color: #fff;
  }
}
@media screen and (min-width: 1200px) and (max-width: 1670px) {
  nav{
    padding-top: 1rem;
  }
  figure{
    margin: auto;
  }
  ul{
    padding-left: 0;
  }
  ul li{
    font-size: .8rem;
  }
  ul li img{
    width: 20px;
  }
}
</style>
