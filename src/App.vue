<template lang="pug">
  v-app(left-fixed-sidebar top-navbar)
  
    main-nav(v-bind:title="title")

    main
      main-side

      v-content
        v-container(fluid)
          
          transition(name="slide" mode="out-in")
            router-view(@view="meta")
    main-footer
</template>

<script>
  export default {
    data () {
      return {
        title: ''
      }
    },

    mounted () {
      this.$vuetify.init()
    },

    methods: {
      meta (obj) {
        if (typeof obj === 'string') {
          return this.title = obj
        }

        this.title = obj.h1
        this.$vuetify.bus.pub('meta:title', obj.title)
        this.$vuetify.bus.pub('meta:description', obj.description)
        this.$vuetify.bus.pub('meta:keywords', obj.keywords)
      }
    }
  }
</script>

<style lang="stylus">
  @import './stylus/main'
</style>