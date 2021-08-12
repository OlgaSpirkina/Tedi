<template>
  <div class="price-container">
    <div class="centered">
      <p
        :price="price"
        :key="price.id"
        v-for="price in totalPrice"
        :class="price.name.toLowerCase()"
      >
          {{price.name}}
          <span>{{price.price}}</span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Total',
  props: {
    totalPrice: Array,
  },
}
</script>

<style scope>
.price-container{
  width: 70%;
  margin: 2rem auto;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  color: var(--tedicolor);
  padding: 1rem;
  box-shadow: 2.5px 2.5px 5px 5px var(--verylightgrey);
}
.centered{
  width: 8vw;
  margin: 0 auto;
}
.centered p{
  display: flex;
  justify-content: space-between;
}
.total{
  font-weight: 600;
  font-size: 1.1rem;
}
@media only screen and (max-width : 800px) {
  .price-container{
    width: 85%;
    height: 5rem;
  }
  .centered{
    width: 80%;
  }
}
@media only screen and (min-width : 801px) and (max-width : 1000px) {
  .price-container{
    width: 80%;
  }
  .centered{
    width: 70%;
  }
}
@media only screen and (min-width : 1001px) and (max-width : 1600px) {
  .centered{
    width: 60%;
  }
}
</style>
