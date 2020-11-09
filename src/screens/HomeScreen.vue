<template>
  <scroll-view>
    <!--
    <nb-list>
      <nb-list-item v-for="meetup in meetups">
        <nb-text>{{meetup.title}}</nb-text>
      </nb-list-item>
    </nb-list>
    -->

      <nb-text class="header-1">Featured Meetups</nb-text>
      <!-- Separate This -->
      <MeetupCard v-for="meetup in meetups"
                  :meetup="meetup"
                  :navigateToDetail="goToMeetupDetail"
                  :key="meetup._id" />
      <!-- Separate This -->
  </scroll-view>
</template>

<script>
import MeetupCard from '@/components/MeetupCard'
export default {
  components: {
    MeetupCard
  },
  props: {
    navigation: {
      type: Object
    }
  },
  data() {
    return {
      title: 'Home Screen!',
    }
  },
  computed: {
    // 5. After mutation we are getting here new dada
    todos () {
      return this.$store.state.todos
    },
    meetups () {
      return this.$store.state.meetups.items
    }
  },
  created () {
    // 1. dispatching fetchTodos, this will call action fetchTodos
    this.$store.dispatch('fetchTodos')
    this.$store.dispatch('meetups/fetchMeetups')
  },
  methods: {
    goToScreen1 () {
      this.navigation.navigate('ScreenOne')
    },
    goToMeetupDetail () {
      this.navigation.navigate('Meetup')
    }
  }
}
</script>
<style>
  .header-1 {
    font-size: 23px;
    padding: 20px;
    font-weight: bold;
  }
</style>