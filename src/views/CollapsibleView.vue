<template lang="pug">
  doc-view(v-bind:doc="doc")
    component-example(header="Accordion")
      div
        v-collapsible
          li(v-for="item in 5")
            v-collapsible-header Item
            v-collapsible-body 
              v-card
                v-card-text(class="grey lighten-3") Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
    component-example(header="Expandable")
      div
        v-collapsible(expand)
          li(v-for="item in 5")
            v-collapsible-header Item
            v-collapsible-body 
              v-card
                v-card-text(class="grey lighten-3") Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
    markup(slot="markup")
      |&lt;v-collapsible&gt;
      |   &lt;v-collapsible-header&gt;Item&lt;/v-collapsible-header&gt;
      |   &lt;v-collapsible-body&gt;
      |     &lt;v-card&gt;
      |       &lt;v-card-text class="grey lighten-3"&gt;...&lt;/v-card-text&gt;
      |     &lt;/v-card&gt;
      |   &lt;/v-collapsible-body&gt;
      |&lt;/v-collapsible&gt;
</template>

<style lang="stylus">
  .component-example
    > div
      width: 100%
</style>

<script>
  export default {
    data () {
      return {
        doc: {
          stage: 'iter',
          title: 'Collapsible',
          desc: `The <code>v-collapsible</code> component is useful for reducing vertical space with large amounts of information. The default functionality of the component is to only display one collapsible body at a time, however, with the <code>expandable</code> property, the collapsible can remain open until explicity closed.`,
          types: [
            'comp', 'slot'
          ],
          params: [
            [
              '<code>&lt;v-collapsible&gt;</code>',
              '',
              'Base component'
            ],
            [
              '<code>expand</code>',
              'Does not contract when multiple are open',
              'Default: false'
            ],
            [
              '<code>&lt;v-collapsible-header&gt;</code>',
              '',
              'Functional component'
            ],
            [
              '<code>&lt;v-collapsible-body&gt;</code>',
              '',
              'Functional component'
            ]
          ]
        }
      }
    },

    mounted () {
      this.$emit('view', this.meta())
    },

    preFetch () {
      return this.methods.meta()
    },

    methods: {
      meta () {
        return {
          title: 'Collapsible Component | Vuetify',
          h1: 'Collapsible',
          description: 'Collapsible component for Vuetify Framework',
          keywords: 'vuetify, collapsible, components'
        }
      }
    }
  }
</script>