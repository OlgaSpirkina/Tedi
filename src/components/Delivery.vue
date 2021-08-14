<template>
  <!-- composant Suivi commande qui contient le dropdown caché -->
  <div class="paragraph-dropdown-track">
    <p>Suivi commande
      <span>
        <i
          @click="displayHidden"
          ref="chevron"
          class="fas fa-chevron-down">
        </i>
      </span>
    </p>
  </div>
  <div ref="hiddenInfo" class="delivery-status hidden-info">
    <!-- les deux premiers checkboxes sont cochés car leurs status est true dans les donnés  -->
    <div
      :status="status"
      :key="status.id"
      v-for="status in deliveryStatus"
      class="img-checkbox"
    >
      <img :src="status.img" alt="status de livraison" />
      <label
        class="switch"
        v-if="status.checked"
        :status="status"
      >
      <!-- si le status.checked est true - checked="checked" par default sinon rien -->
        <input
          type="checkbox"
          v-model="status.checked"
        />
        <!-- styliser avec une icone -->
        <span class="styled_checkbox">
          <i
          ref="icon"
          class="fas fa-check outline_check_icon"></i>
        </span>
      </label>
      <!-- la partie else de la condition pour vérifier si le checkbox est cocher par default ou non -->
      <label class="switch" v-else>
        <input
          type="checkbox"
          v-model="status.checked"
        />
        <span class="styled_checkbox"></span>
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Delivery',
  props: {
    deliveryStatus: Array,
  },
  methods: {
    // faire apparaitre ou disparaitre le dropdown caché et faire bouger l'icon du chevron: ouvert/fermé
    displayHidden () {
      const hiddenInfo = this.$refs.hiddenInfo.classList
      const chevron = this.$refs.chevron.classList
      hiddenInfo.contains('hidden-info') ? hiddenInfo.remove('hidden-info') : hiddenInfo.add('hidden-info')
      chevron.contains('turn_around') ? chevron.remove('turn_around') : chevron.add('turn_around')
    },
  },
}
</script>

<style scope>
.img-checkbox{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-end;
}
.img-checkbox img{
  margin: 1rem 0;
}
/* Début du style des icons de l'input coché */
.switch{
  position: relative;
  display: inline-block;
  width: 1.5rem;
  height: 1.5rem;
}
.switch input{
  opacity: 0;
  width: 0;
  height: 0;
}
.styled_checkbox{
  margin: 0 auto;
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border: 1px solid grey;
}
.outline_check_icon{
  z-index: 1;
  width: 1.5rem;
  font-size: 1.5rem;
  color: #006e42;
  border: 1px solid #006e42;
  border-radius: 50%;
}
/* fin des icons stylisés des checkbox */
/* la partie cachée avec les images et checkboxes */
.delivery-status{
  display: flex;
  justify-content: space-between;
  width: 30vw;
  margin: 1rem 0;
}
.hidden-info{
  display: none;
}
/* icon open/closed */
.fa-chevron-down{
  position: relative;
  float: right;
}
.turn_around{
  transform: rotate(180deg);
}
.paragraph-dropdown-track{
  border-top: 1px solid;
  padding-top: .5rem;
}
@media only screen and (max-width : 1400px) {
  .paragraph-dropdown-track{
    width: 100%;
    }
  .delivery-status{
    width: 100%;
  }
}
</style>
