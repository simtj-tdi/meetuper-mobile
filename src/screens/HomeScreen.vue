<template>
  <scroll-view>
    <nb-list>
      <nb-list-item v-for="todo in todos">
        <nb-text>{{todo.title}}</nb-text>
      </nb-list-item>
    </nb-list>
  </scroll-view>
</template>

<script>

export default {
  props: {
    navigation: {
      type: Object
    }
  },
  data() {
    return {
      title: 'Home Screen!'
    }
  },
  computed: {
    // 5. After mutation we are getting here new dada
    todos () {
      return this.$store.state.todos
    }
  },
  created () {
    // 1. dispatching fetchTodos, this will call action fetchTodos
    this.$store.dispatch('fetchTodos')
  },
  methods: {
    goToScreen1 () {
      this.navigation.navigate('ScreenOne')
    }
  }
}
</script>
