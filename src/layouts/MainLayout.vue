<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-dark">
      <q-toolbar class="q-ma-xs">
        <q-toolbar-title class="text-center text-accent">
          <div class="text-h4 text-accent">Jose Solano Orea</div>
          <div class="text-subtitle2 text-accent">02/07/1952 - 08/05/2020</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-header>
    <q-page-container class="q-mt-none">
      <router-view />
      <Slider></Slider>
      <Cards></Cards>
      <Footer></Footer>
    </q-page-container>
  </q-layout>
</template>

<script>
import Slider from 'pages/Slider'
import Cards from 'pages/Cards'
import Footer from 'pages/Footer'
export default {
  name: 'MainLayout',
  components: {
    Slider,
    Cards,
    Footer
  }
}
</script>
