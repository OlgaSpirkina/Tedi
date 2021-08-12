<template>
  <div class="visa-cb">
    <img :src="visaPath" alt="logo Visa"/>
    <p>{{title}}</p>
  </div>
</template>

<script>
export default {
  name: 'PaymentInfo',
  props: {
    visaPath: String,
    title: String,
  },
}
</script>

<style scope>
.visa-cb{
  width: 70%;
  margin: 2rem auto;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  color: var(--tedicolor);
  padding: 1rem;
  box-shadow: 2.5px 2.5px 5px 5px var(--verylightgrey);
}

.visa-cb img{
  width: 5rem;
  margin-right: .5rem;
}
@media only screen and (max-width : 800px) {
  .visa-cb{
    width: 85%;
    height: 4rem;
  }
}
@media only screen and (min-width : 801px) and (max-width : 1000px) {
  .visa-cb{
    width: 80%;
  }
}
</style>
