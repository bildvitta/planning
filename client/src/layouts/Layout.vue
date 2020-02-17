<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title>Planning Poker</q-toolbar-title>

        <!-- <q-btn flat round>
          <q-avatar color="white" size="32px" text-color="primary">W</q-avatar>
        </q-btn> -->
      </q-toolbar>

      <q-toolbar v-if="hasTabs">
        <q-tabs class="full-width" align="center">
          <q-route-tab v-for="(tab, index) in tabs" :key="index" v-bind="tab" exact />
        </q-tabs>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  computed: {
    tabs () {
      const tabs = [
        { label: 'Padrão', to: '' },
        { label: 'Camiseta', to: '/?type=tshirt' },
        { label: 'Fibonacci', to: '/?type=fibonacci' },
        { label: 'Risco', to: '/?type=risk' }
      ]

      return tabs
    },

    hasTabs () {
      return !!this.tabs.length
    }
  }
}
</script>
