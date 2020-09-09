<template>
  <div :class="['todo-item', todo.completed ? 'completed' : '']">
    <input type="checkbox" class="check" v-model="todo.completed" />
    <label>{{todo.content}}</label>
    <button @click="delItem"></button>
  </div>
</template>

<script>
  export default {
    name: 'ListItem',
    props: {
      todo: Object,
    },
    methods: {
      delItem() {
        this.$emit('del', this.todo.id)
      },
    },
  }
</script>

<style lang="stylus" scoped>
  @import '~styles/global.styl'
  @import '~styles/mixins.styl'

  .todo-item
    display: flex
    padding: 10px
    border-bottom: 0.5px solid rgba(0, 0, 0, 0.1)
    font-size: 22px
    justify-content: space-between
    color: rgb(80, 80, 80)

    &:hover
      button:after
        content: '×'
        font-size: 29px
        color: $myColor
        z-index: 1000
        font-weight: bold

    &.completed
      color: #d9d9d9
      text-decoration: line-through

    input
      width: 50px
      height: 30px
      text-align: center
      cleanDefaultStyle()

      &:after
        content: url('~images/unchecked.svg')

      &:checked:after
        content: url('~images/checked.svg')

    label
      flex: 1

    button
      width: 40px
      background: transparent
      cleanDefaultStyle()
      cursor: pointer
</style>