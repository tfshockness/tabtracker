<template>
  <v-app>
    <main>

      <ts-nav></ts-nav>

      <v-container fluid>
        <router-view></router-view>
      </v-container>

      <ts-footer></ts-footer>

    </main>
  </v-app>


</template>

<script>
  import Navigation from './components/layout/Navigation.vue'
  import Footer from './components/layout/Footer.vue'
export default {
  name: 'app',
    components: {
      'ts-nav': Navigation,
        'ts-footer': Footer
    }
}
</script>

<style>

</style>
