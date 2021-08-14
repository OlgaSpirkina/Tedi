<template>
  <div class="help-dropdown">
    <div
      :help="help"
      :key="help.id"
      v-for="help in helpSection"
      class="paragraph-dropdown"
    >
      <p>
        {{help.name}}
        <i
          @click="toggle($event, help.id)"
          class="fas fa-chevron-down">
        </i>
      </p>
      <div
        :class="{info_hidden: !help.visible}">
        {{help.info}}
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Help',
  data(){
    return{
      helpSection:[
        {
          "id": 0,
          "name": "FOIRE AUX QUESTIONS TEDIBER",
          "info": "I'm baby bitters sustainable activated charcoal, listicle authentic flannel intelligentsia vinyl 90's asymmetrical fingerstache narwhal thundercats. Shaman gochujang prism, pork belly ramps PBR&B 8-bit.",
          "visible": false
        },
        {
          "id": 1,
          "name": "LA GARANTIE TEDIBER",
          "info": "Live-edge mixtape succulents kale chips keffiyeh. Seitan fam tacos echo park put a bird on it irony keffiyeh semiotics cold-pressed. Gentrify tilde hell of succulents deep v hot chicken trust fund cardigan flannel vexillologist four dollar toast.",
          "visible": false
        },
        {
          "id": 2,
          "name": "REPRISE DE L’ANCIENNE LITERIE",
          "info": "Brooklyn snackwave single-origin coffee gentrify, succulents pinterest disrupt shaman. Coloring book pickled man braid shabby chic before they sold out craft beer sartorial man bun air plant knausgaard woke.",
          "visible": false
        },
        {
          "id": 3,
          "name": "COMMENT FAIRE UN RETOUR ?",
          "info": "Keffiyeh art party pop-up kinfolk yuccie poutine church-key woke bushwick pinterest whatever. Intelligentsia cred pork belly 3 wolf moon ugh XOXO tacos humblebrag banh mi normcore truffaut.",
          "visible": false
        }
      ]
    }
  },
  methods: {
    // faire apparaitre ou disparaitre le dropdown caché et faire bouger l'icon du chevron: ouvert/fermé
    toggle: function( event, id ) {
      event.target.classList.toggle('is-open')
      this.helpSection.map(help => help.id === id ? help.visible = !help.visible : help)
    },
  },
}
</script>

<style scope>
/* la class pour faire pivoter l'icone du chevron */
.is-open{
  display: block;
  transform: rotate(180deg);
}
/* la div avec le contenu caché */
.info_hidden{
  display: none;
}
/* la div principale de la section */
.help-dropdown{
  width: 70%;
  margin: 2rem auto;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: var(--tedicolor);
}
/* la div pour chaque paragraph et son contenu caché */
.paragraph-dropdown{
  margin: 0;
  padding: 1rem 0;
  width: 100%;
  border-bottom: 1px solid;
  border-top: none;
}
.paragraph-dropdown div{
  margin: 1rem 0;
}
.paragraph-dropdown p{
  width: inherit;
  margin: 0;
  border-bottom: none;
}
/* icone du chevron ouvrant les détails */
.fas{
  font-size: 1.5rem;
}
@media only screen and (max-width : 550px) {
  .help-dropdown{
    width: 90%;
    margin-bottom: 4rem;
  }
}
@media only screen and (min-width : 551px) and (max-width : 800px) {
  .help-dropdown{
    width: 80%;
    margin: 0 auto;
    margin-bottom: 4rem;
  }
}
@media only screen and (min-width : 801px) and (max-width : 1000px) {
  .help-dropdown{
    margin-top: 2rem;
    width: 70%;
  }
  .paragraph-dropdown{
    width: 100%;
  }
}
@media only screen and (min-width : 1001px) and (max-width : 1400px) {
  .help-dropdown{
    margin-top: 3rem;
  }
}

</style>
