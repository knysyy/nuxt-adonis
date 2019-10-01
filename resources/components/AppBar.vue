<template>
  <v-app-bar app flat>
    <v-toolbar-title>
      <v-btn dark icon @click.stop="onClick">
        <v-icon>mdi-view-list</v-icon>
      </v-btn>
      {{ title }}
    </v-toolbar-title>
  </v-app-bar>
</template>

<script>
import { mapMutations } from 'vuex'

export default {
  data: () => ({
    title: null
  }),
  watch: {
    $route(val) {
      this.title = val.name
    }
  },
  created() {
    this.title = this.$route.name
  },
  methods: {
    ...mapMutations('app', ['setDrawer', 'toggleDrawer']),
    onClick() {
      this.setDrawer(!this.$store.state.app.drawer)
    }
  }
}
</script>
