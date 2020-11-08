<template>
  <v-app class="grey lighten-4">
    <Navbar />

    <v-content class="mx-4 mb-4">
      <router-view></router-view>
    </v-content>
    
  </v-app>
</template>

<script>
import Navbar from './components/Navbar'
import Darkmode from 'darkmode-js';

const options = {
  bottom: '20px', // default: '32px'
  right: '32px', // default: '32px'
  left: 'unset', // default: 'unset'
  time: '0.5s', // default: '0.3s'
  mixColor: '#fff', // default: '#fff'
  backgroundColor: '#fff',  // default: '#fff'
  buttonColorDark: '#000',  // default: '#100f2c'
  buttonColorLight: '#fff', // default: '#fff'
  saveInCookies: true, // default: true,
  label: '🌓', // default: ''
  autoMatchOsTheme: true // default: true
}

const darkmode = new Darkmode(options);
darkmode.showWidget();



export default {
  components: { Navbar },
  name: 'App',
  data () {
    return {
      
    }
  }
}
</script>


<style>
.darkmode-layer, .darkmode-toggle {
  z-index: 500;
}

body.darkmode--activated aside.v-navigation-drawer {
  background: #87264b !important;
}

body.darkmode--activated aside.v-navigation-drawer button{
  background: #fff !important;
  color: white !important;
}

body.darkmode--activated aside.v-navigation-drawer button div{
  color: #bd4472 !important;
}

.darkmode--activated img {
    filter: invert(1);
}
</style>