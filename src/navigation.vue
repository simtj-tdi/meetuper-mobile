<template>
  
      <Root>
        <AppNavigation />
      </Root>
  
</template>

<script>
  import HomeScreen from '@/screens/HomeScreen'
  import MeetupDetailScreen from '@/screens/MeetupDetailScreen'
  import Screen1 from '@/screens/Screen1'
  import Screen2 from '@/screens/Screen2'
  import Screen3 from '@/screens/Screen3'
  import { Root } from 'native-base';

  import { createAppContainer,
           createBottomTabNavigator,
           createDrawerNavigator,
           createStackNavigator,
           } from "vue-native-router";

  const HomeStack = createStackNavigator(
      {
          Home: HomeScreen,
          Meetup: MeetupDetailScreen,
          ScreenOne: Screen1
      },
      {
        initialRouteName: 'Home',
      }
  )
  
  const SomeOtherStack = createStackNavigator({
      Screen2
  }, {
      headerMode: 'none',
      navigationOptions: {
          headerVisible: false
      }
  })

  const SomeOtherOtherStack = createStackNavigator({
      Screen3
  }, {
      headerMode: 'none',
      navigationOptions: {
          headerVisible: false
      }
  })

  const DrawerNavigation = createDrawerNavigator({
      DrawerStack1: SomeOtherStack,
      DrawerStack2: SomeOtherOtherStack
  })

  const TabNavigation = createBottomTabNavigator({
      Meetups: HomeStack,
      Other: DrawerNavigation
  })

  const AppNavigation = createAppContainer(TabNavigation)

  export default {
    components: {
      AppNavigation, Root
    }
  }
</script>


