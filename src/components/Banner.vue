<template>
  <div class="banner-container">
    <div class="heading-style">
      <span class="style-line"></span><h2>{{title.toUpperCase()}}</h2><span class="style-line"></span>
    </div>
    <img class="zigzag-line" src="https://raw.githubusercontent.com/OlgaSpirkina/TediBer/b237b50975b848e8da759a48009c1f1b512c9787/public/zigzag.svg" alt="zigzag line" />
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
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 3rem 0;
}
.banner-container:first-of-type{
  margin-top: 10rem;
}
.heading-style{
  width: 90vw;
  display: flex;
  justify-content: center;
}
.style-line{
  width: 50vw;
  height: 5vh;
  border-top: 1px solid var(--tedicolor);
  margin-top: .5rem;
}
h2 {
  width: 100%;
  text-align: center;
  line-height: 0.1em;
  margin: 0 auto;
  letter-spacing: 3px;
  font-weight: 400;
  color: var(--tedicolor);
}
.zigzag-line{
  width: 7vw;
}
@media only screen and (max-width : 550px) {
  .banner-container{
    height: inherit;
  }
  .style-line{
    width: 15vw;
  }
  .zigzag-line{
    width: 35vw;
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
  h2{
    width: 100%;
    line-height: 1.2rem;
  }
  .style-line{
    width: 15vw;
  }
}
@media only screen and (min-width : 1201px) and (max-width: 1400px) {
  h2{
    width: 90%;
  }
  .zigzag-line{
    width: 20vw;
    margin-top: 1rem;
  }
}

</style>
