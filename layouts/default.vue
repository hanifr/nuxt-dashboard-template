<template>
  <v-app>
    <v-main>
      <Navbar/>
      <div id="router_view">
        <Nuxt />
      </div>
    </v-main>
    <v-footer
      app
    >
      <v-col
      class="text-center"
      cols="12"
    >
       <strong>Sports Engineering and Artificial Intelligence Centre, UiTM Shah Alam © Copyright {{ new Date().getFullYear() }} </strong>
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout'
}
</script>
