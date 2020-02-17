<template>
  <q-card class="text-white" :class="classes">
    <q-responsive :ratio="12/16">
      <q-card-section class="flex flex-center">
        <strong v-if="options.text" class="text-h1">{{ options.text }}</strong>
      </q-card-section>
    </q-responsive>
  </q-card>
</template>

<script>
export default {
  props: {
    options: {
      default: () => ({}),
      type: Object
    }
  },

  computed: {
    classes () {
      return `bg-${this.options.color || 'primary'}`
    }
  }
}
</script>
