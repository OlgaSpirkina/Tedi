<template>
  <div >
    <div
      :item="item"
      :key="item.id"
      class="item_dropdown"
      v-for="item in helpSection"
    >
      <p
        class="item_paragraph">{{item.name}}</p>
      <i
        @click="hiddenParagraph"
        ref="chevronDown"
        class="fas fa-chevron-down">
      </i>
    </div>
    <div
      ref="infoHidden"
      class="info-hidden">
      {{item.info}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'Help',
  props: {
    helpSection: Array,
  },
  methods: {
    // faire apparaitre ou disparaitre le dropdown caché et faire bouger l'icon du chevron: ouvert/fermé
    hiddenParagraph () {
      const infoHidden = this.$refs.infoHidden.classList
      const chevronDown = this.$refs.chevronDown.classList
      infoHidden.contains('info-hidden') ? infoHidden.remove('info-hidden') : infoHidden.add('info-hidden')
      chevronDown.contains('turn_around') ? chevronDown.remove('turn_around') : chevronDown.add('turn_around')
    },
  },
}
</script>

<style scope>
.turn_around{
  transform: rotate(180deg);
}
.info-hidden{
  display: none;
}
</style>
