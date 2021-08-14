<template>
  <div class="banner-container">
    <div class="heading-style">
      <span class="style-line"></span><h2>{{title.toUpperCase()}}</h2><span class="style-line"></span>
    </div>
    <img class="zigzag-line" src="../assets/zigzag.svg" alt="zigzag line" />
  </div>
</template>

<script>
export default {
  name: 'Banner',
  props: ['title'],
  components: {
  },
}
</script>

<style scope>
.banner-container{
  width: 70vw;
  margin: 0 auto;
  margin-top: 4rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.banner-container:first-of-type{
  margin-top: 11rem;
}
/* le texte et les deux spans de chaque côté du texte pour créer deux lignes horizontales */
.heading-style{
  width: 70vw;
  display: flex;
  justify-content: center;
}
/* les lignes horizontales de chaque côté du texte */
.style-line{
  width: 50vw;
  border-top: 1px solid var(--tedicolor);
  margin-top: .5rem;
}
h2 {
  width: 100%;
  text-align: center;
  line-height: 1.5rem;
  margin: 0 auto;
  letter-spacing: 3px;
  font-weight: 400;
  color: var(--tedicolor);
}
.zigzag-line{
  width: 7vw;
  margin-top: 1rem;
}
@media only screen and (max-width : 550px) {
  .banner-container{
    width: 90%;
    height: inherit;
  }
  .banner-container:first-of-type{
    margin-top: 15rem;
  }
  .heading-style{
    width: 100%;
  }
  .zigzag-line{
    width: 30vw;
    margin-top: 0;
  }
  h2{
    display: inline-block;
    line-height: 1.5rem;
    font-size: 1.5rem;
    letter-spacing: 3px;
    width: 100%;
  }
}
@media only screen and (min-width : 551px) and (max-width : 1200px) {
  .zigzag-line{
    width: 15vw;
    margin-top: .5rem;
  }
  .banner-container{
    width: 90%;
    height: inherit;
  }
  h2{
    width: 100%;
  }
  .heading-style{
    width: 100%;
  }
}
@media only screen and (min-width : 1201px) and (max-width: 1400px) {
  .zigzag-line{
    width: 10vw;
    margin-top: 1rem;
  }
}

</style>
