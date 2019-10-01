<template>
  <v-app dark>
    <v-container fill-height style="height: calc(100vh - 58px);">
      <v-layout align-center>
        <v-flex text-center>
          <template v-if="error.statusCode === 404">
            <h1 class="display-2 primary--text">{{ pageNotFound.title }}</h1>
            <p>{{ pageNotFound.text }}</p>
          </template>
          <template v-else>
            <h1 class="display-2 primary--text">{{ otherError.title }}</h1>
            <p>{{ otherError.text }}</p>
          </template>
          <v-btn to="/" outlined color="primary">
            Home
          </v-btn>
        </v-flex>
      </v-layout>
    </v-container>
  </v-app>
</template>

<script>
export default {
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  head() {
    const title =
      this.error.statusCode === 404
        ? this.pageNotFound.title
        : this.otherError.title
    return {
      title
    }
  },
  data() {
    return {
      pageNotFound: {
        title: '404 Not Found',
        text: 'The page you were looking for does not exist'
      },
      otherError: {
        title: 'An Error Occurred',
        text: 'It looks like an error has occurred'
      }
    }
  }
}
</script>
