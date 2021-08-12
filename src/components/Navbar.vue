<template>
  <nav>
    <ul class="container-horizontal" ref="nav">
      <li :key="task.id" v-for="task in tasks">
        <div
          v-if="task.title.includes('https')"
          :task="task">
          <img :src="task.title" :style="{width: '10rem'}" alt="logo tediber" class="image-display" />
        </div>
        <div
          v-else-if="task.content !== null"
          @mouseenter="$event.currentTarget.style.color = '#999'"
          @mouseleave="$event.currentTarget.style.color = '#000'"
        >
          {{task.title}}<i class="fas fa-chevron-down"
            @mouseenter="$event.currentTarget.style.color = '#999'"
            @mouseleave="$event.currentTarget.style.color = '#000'"
          ></i>
          <div
            ref="products" class="sub-menu">
              <small
              :key="index" v-for="(sub, index) in task.content"
              >{{sub}}</small>
            </div>
        </div>
        <div
          @mouseenter="$event.currentTarget.style.color = '#999'"
          @mouseleave="$event.currentTarget.style.color = '#000'"
          v-else
        >
          {{task.title}}
        </div>
      </li>
    </ul>
  </nav>
  <i @click="toggleNav" class="fa fa-bars"></i>
</template>
<script>
export default {
  name: 'Navbar',
  props: {
    tasks: Array,
  },
  methods: {
		toggleNav () {
			const nav = this.$refs.nav.classList
			nav.contains('container-horizontal') ? nav.remove('container-horizontal') : nav.add('container-horizontal')
      nav.contains('vertical') ? nav.remove('vertical') : nav.add('vertical')
		},
    // toggleSubMenu(){
    //   const products = this.$refs.products.classList
    //   products.contains('sub-menu') ? products.remove('sub-menu') : products.add('sub-menu')
    // }
	}
}


</script>

<style scoped>
nav{
  position: sticky;
}
.image-display{
  display: inline-block;
}
.image-hidden{
  display: none;
}
.sub-menu{
  display: none;
}
.container-horizontal img{
  display: inline-block;
}
.vertical{
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}
.vertical img{
  display: none;
}
ul li{
  list-style: none;
}
a{
  text-decoration: none;
  color: inherit;
}
@media screen and (max-width: 759px) {
  ul{
    flex-direction: column;
    align-items: flex-start;
    margin: 1rem 0;
  }
}
</style>
