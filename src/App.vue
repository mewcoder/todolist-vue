<template>
  <div>
    <TodoHeader></TodoHeader>
    <ListBox></ListBox>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
  import TodoHeader from './components/Header'
  import ListBox from './components/List/ListBox'
  import TodoFooter from './components/Footer'

  export default {
    name: 'App',
    components: {
      TodoHeader,
      TodoFooter,
      ListBox,
    },
  }
</script>

<style lang="stylus" scoped></style>