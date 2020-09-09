<template>
  <div class="header">
    <h1>TO DO LIST</h1>
  </div>
</template>

<script>
  export default {
    name: 'TodoHeader',
  }
</script>

<style lang="stylus" scoped>
  @import '~styles/global.styl'

  .header
    text-align: center

    h1
      font-size: 50px
      font-weight: 800
      color: $myColor
      text-shadow: 4px 4px 4px #222
</style>