<template>
  <div
    v-if="task.title.includes('https')"
    ref="img" class="image-display"
    :task="task">
    <a :href="task.path" >
      <img :src="task.title" :style="{width: '10rem'}" alt="logo tediber"/>
    </a>
  </div>
  <div
    @mouseenter="$event.currentTarget.style.color = '#999'"
    @mouseleave="$event.currentTarget.style.color = '#000'"
    v-else>
    <a :href="task.path">
      {{task.title}}
    </a>
  </div>
</template>

<script>
export default {
  name: 'NavbarItem',
  props: {
    task: Object,
  },
}
</script>

<style scope>

</style>
