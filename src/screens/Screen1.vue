<template>
  <view class="container">
    <text class="text-color-primary">{{title}}</text>
    <button :title="'Go To Screen 2'" :on-press="goToScreen2" />
  </view>
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
      title: 'I AM SCREEN 1'
    }
  },
  methods: {
    goToScreen2 () {
      this.navigation.navigate('Screen2')
    }
  }

}
</script>

