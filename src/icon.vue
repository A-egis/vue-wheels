<template>
  <svg class="w-icon">
    <use :xlink:href="`#i-${name}`"></use>
  </svg>
</template>

<script>
export default {
  props: ['name']
}
</script>

<style lang="scss">
.w-icon {
  width: 1em;
  height: 1em;
}
</style>