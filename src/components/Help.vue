<template>
  <div class="help_dropdown">
    <div
      :help="help"
      :key="help.id"
      v-for="help in helpSection"
    >
      <p v-if="help.id != 0">{{help.name}}</p>
      <i
        @click="toggle"
        :ref="'chevronDown-' + help.id"
        class="fas fa-chevron-down">
      </i>
      <div
        :ref="'infoHidden-' + help.id"
        class="info-hidden">
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
          "name": "FOIRE AUX QUESTIONS TEDIBER",
          "info": "I'm baby bitters sustainable activated charcoal, listicle authentic flannel intelligentsia vinyl 90's asymmetrical fingerstache narwhal thundercats. Shaman gochujang prism, pork belly ramps PBR&B 8-bit."
        },
        {
          "name": "LA GARANTIE TEDIBER",
          "info": "Live-edge mixtape succulents kale chips keffiyeh. Seitan fam tacos echo park put a bird on it irony keffiyeh semiotics cold-pressed. Gentrify tilde hell of succulents deep v hot chicken trust fund cardigan flannel vexillologist four dollar toast."
        },
        {
          "name": "REPRISE DE L’ANCIENNE LITERIE",
          "info": "Brooklyn snackwave single-origin coffee gentrify, succulents pinterest disrupt shaman. Coloring book pickled man braid shabby chic before they sold out craft beer sartorial man bun air plant knausgaard woke."
        },
        {
          "name": "COMMENT FAIRE UN RETOUR ?",
          "info": "Keffiyeh art party pop-up kinfolk yuccie poutine church-key woke bushwick pinterest whatever. Intelligentsia cred pork belly 3 wolf moon ugh XOXO tacos humblebrag banh mi normcore truffaut."
        }
      ]
    }
  },
  methods: {
    // faire apparaitre ou disparaitre le dropdown caché et faire bouger l'icon du chevron: ouvert/fermé
    toggle: function( event ) {
      event.target.classList.toggle('is-open')
   }
  },
}
</script>

<style scope>
.turn_around{
  transform: rotate(180deg);
}
.is-open{
  display: block;
  transform: rotate(180deg);
}
.info-hidden{
  display: none;
}
.help_dropdown{
  width: 70%;
  margin: 2rem auto;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: var(--tedicolor);
  box-shadow: 2.5px 2.5px 5px 5px var(--verylightgrey);
}
.help_dropdown div{
  margin: 0;
  padding: 1rem 0;
  width: 100%;
}
/* icone du chevron ouvrant les détails */
.help_dropdown div span{
  font-size: 1.5rem;
}
.help_dropdown div p{
 width: inherit;
}
</style>
