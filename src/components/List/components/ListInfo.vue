<template>
  <div class="todo-info">
    <span class="total">{{ctotal}} 个未完成</span>
    <div class="tabs">
      <a
        class="btn"
        v-for="(item,index) in states"
        :key="index"
        :class="['btn-primary',state == item ? 'actived':'']"
        @click="toggle(item)"
      >{{item}}</a>
    </div>
    <button class="btn-info" @click="clear">清除已完成</button>
  </div>
</template>

<script>
  export default {
    name: 'ListInfo',
    props: {
      ctotal: Number,
    },
    data() {
      return {
        states: ['全部', '未完成', '已完成'],
        state: '全部',
      }
    },
    methods: {
      clear() {
        console.log('clear')
        this.$emit('clear')
      },
      toggle(state) {
        this.state = state
        this.$emit('toggle', state)
      },
    },
  }
</script>

<style lang="stylus" scoped>
  @import '~styles/global.styl'
  @import '~styles/mixins.styl'

  .todo-info
    display: flex
    justify-content: space-between
    padding: 5px 10px
    text-align: center
    border-top: 1px solid rgba(0, 0, 0, 0.1)
    height: 30px

    .total
      color: $myColor

    .tabs
      display: flex
      justify-content: space-between
      width: 220px
      text-align: center

    .btn-primary
      primaryBtn()

      &.actived
        activeBtn()

    .btn-info
      activeBtn()
</style>