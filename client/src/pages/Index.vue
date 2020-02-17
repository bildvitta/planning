<template>
  <q-page padding>
    <div class="row q-col-gutter-sm">
      <div v-for="(options, index) in cards" :key="index" class="col-6 col-sm-4 col-md-3 col-lg-2">
        <poker-card class="cursor-pointer" :options="options" @click.native="openCard(options)" />
      </div>
    </div>

    <q-dialog v-model="modalCard">
      <poker-card class="full-width" :options="modalCardOptions" />
    </q-dialog>
  </q-page>
</template>

<script>
import PokerCard from 'components/PokerCard'

const common = [
  { text: '∞' },
  { text: '?' },
  { text: '☕' }
]

const standard = [
  { text: '0' },
  { text: '½' },
  { text: '1' },
  { text: '2' },
  { text: '3' },
  { text: '5' },
  { text: '8' },
  { text: '13' },
  { text: '20' },
  { text: '40' },
  { text: '100' },
  ...common
]

const tshirt = [
  { text: 'PP' },
  { text: 'P' },
  { text: 'M' },
  { text: 'G' },
  { text: 'GG' },
  { text: 'XG' },
  ...common
]

const fibonacci = [
  { text: '0' },
  { text: '1' },
  { text: '2' },
  { text: '3' },
  { text: '5' },
  { text: '8' },
  { text: '13' },
  { text: '21' },
  { text: '34' },
  { text: '55' },
  { text: '89' },
  { text: '144' },
  ...common
]

const risk = [
  { color: 'green-10' },
  { color: 'yellow-7' },
  { color: 'brown' },
  { color: 'purple' },
  { color: 'red' },
  ...common
]

const types = {
  standard,
  tshirt,
  fibonacci,
  risk
}

export default {
  components: {
    PokerCard
  },

  data () {
    return {
      modalCard: false,
      modalCardOptions: {}
    }
  },

  computed: {
    cards () {
      return types[this.type] || standard
    },

    type () {
      return this.$route.query.type
    }
  },

  methods: {
    openCard (options) {
      this.modalCardOptions = options
      this.modalCard = true
    }
  }
}
</script>

<style lang="scss">
  .q-dialog__backdrop {
    background-color: white;
  }
</style>
