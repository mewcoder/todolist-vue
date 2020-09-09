<template>
  <div class="list">
    <input
      type="text"
      class="add-todo"
      placeholder="输入待办事项..."
      autofocus
      v-model="content"
      @keyup.enter="addTodo"
    />

    <ListItem
      v-for="(item,index) in filterData"
      :key="index"
      :todo="item"
      @del="handleDel"
    ></ListItem>
    <ListInfo :ctotal="total" @toggle="handleToggle" @clear="handleClear"></ListInfo>
  </div>
</template>

<script>
  import ListInfo from './components/ListInfo.vue'
  import ListItem from './components/ListItem.vue'
  let id = 0
  export default {
    name: 'ListBox',
    components: {
      ListInfo,
      ListItem,
    },
    data() {
      return {
        todoData: [],
        content: '',
        total: 0,
        filter: '全部',
      }
    },
    methods: {
      addTodo() {
        if (this.content === '') return

        this.todoData.unshift({
          id: id++,
          content: this.content,
          completed: false,
        })
        this.content = ''
      },
      handleDel(id) {
        this.todoData.splice(
          this.todoData.findIndex((item) => item.id === id),
          1
        )
      },
      handleToggle(state) {
        this.filter = state
      },
      handleClear() {
        this.todoData = this.todoData.filter((item) => item.completed == false)
      },
    },
    watch: {
      todoData: {
        deep: true,
        handler() {
          this.total = this.todoData.filter(
            (item) => item.completed == false
          ).length
        },
      },
    },
    computed: {
      filterData() {
        switch (this.filter) {
          case '全部':
            return this.todoData
            break
          case '未完成':
            return this.todoData.filter((item) => item.completed == false)
            break
          case '已完成':
            return this.todoData.filter((item) => item.completed == true)
            break
        }
      },
    },
  }
</script>

<style lang="stylus" scoped>
  @import '~styles/global.styl'

  .list
    margin: 0 auto
    width: 600px
    background-color: #fff
    box-shadow: 0 0 5px $myColor
    border-radius: 5px

    .add-todo
      cleanDefaultStyle()
      border-radius: 5px
      padding: 16px 16px 16px 16px
      width: 100%
      font-size: 24px
      box-sizing: border-box
      border-color: $myColor
</style>