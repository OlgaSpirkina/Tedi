<template>
  <div className="paragraph_dropdown">
    text
    <span>
      <i
        @click="displayHidden"
        class="fas fa-chevron-down"></i>
    </span>
  </div>
  <div ref="hiddenInfo" class="hidden-info">
    <Delivery/>
  </div>
</template>

<script>
import Delivery from './Delivery.vue'
export default {
  name: 'Dropdown',
  props: {
  },
  components: {
    Delivery,
  },
  methods: {
    displayHidden () {
			const hiddenInfo = this.$refs.hiddenInfo.classList
			hiddenInfo.contains('hidden-info') ? hiddenInfo.remove('hidden-info') : hiddenInfo.add('hidden-info')
    },
  },
}
</script>

<style scope>

</style>
