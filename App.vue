<template>
  <App v-if="isAppReady" />
</template>

<script>
  import * as Font from "expo-font";
  import { Ionicons } from '@expo/vector-icons'
  import App from './src'

  export default {
    components: { 
      App
    },
    data() {
        return {
            isAppReady: false
        }
    },
    async created () {
      try {
        await Font.loadAsync({
            // Roboto: require("./node_modules/native-base/Fonts/Roboto.ttf"),
            // Roboto_medium: require("./node_modules/native-base/Fonts/Roboto_medium.ttf"),
            // Ionicons: require("./node_modules/@expo/vector-icons/build/vendor/react-native-vector-icons/Fonts/Ionicons.ttf"),
            Roboto: require('native-base/Fonts/Roboto.ttf'),
            Roboto_medium: require('native-base/Fonts/Roboto_medium.ttf'),
            ...Ionicons.font,
        });

        this.isAppReady = true
      } catch (error) {
        console.log("some error occured", error);
        // this.isAppReady = true;
      }
    }
  }
</script>
