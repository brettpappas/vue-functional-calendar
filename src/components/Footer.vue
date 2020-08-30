<template>
  <div class="footerContainer">
    <slot name="cleaner"></slot>
    <slot name="footer"></slot>
  </div>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style scoped lang="postcss">
.footerContainer {
  display: flex;
  justify-content: space-between;
  margin: 0 20px 20px;
}
</style>
