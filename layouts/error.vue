<template>
  <v-container
    class="text-center"
    fill-height
    style="height: calc(100vh - 58px);"
  >
  <v-img
    :src="require('~/assets/images/background/404.png')" contain aspect-ratio="3.0">
    <v-row align="center">
      <v-col>
      <h1 
      v-if="error.statusCode === 404"
      class="display-2 primary--text font-weight-bold"
      >
      {{ pageNotFound }}
    </h1>
    <h1 v-else>
      {{ otherError }}
    </h1>
    <p class="title font-weight-bold">The page you were looking for does not exist</p>
      <v-btn
          :to="`/`"
          color="primary"
          outlined
          class="title font-weight-bold"
        >
          Get me out of here!
        </v-btn>
      </v-col>
    </v-row>
  </v-img>
  </v-container>
</template>

<script>
  export default {
    name: 'FourOhFour',
    props: {
    error: {
      type: Object,
      default: null
    }
  },
  data () {
    return {
      pageNotFound: 'Whoops, 404',
      otherError: 'An error occurred'
    }
  },
  head () {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title
    }
  }
}
</script>