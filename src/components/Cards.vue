<template lang="html">
  <div class="">
    <sport-card v-if="list.type==='sport'" :list="list" :score-sports="scoreSports"></sport-card>
    <pic-card v-if="list.type==='Picture'" :list="list"></pic-card>
    <program-card v-if="list.type==='Program'" :list="list"></program-card>
  </div>
</template>

<script>
import PicCard from './PicCard'
import SportCard from './SportCard'
import ProgramCard from './ProgramCard'
export default {
  props: ['list', 'scoreSports'],
  data () {
    return {
    }
  },
  methods: {
  },
  components: {
    PicCard,
    SportCard,
    ProgramCard
  }
}
</script>

<style lang="css">

</style>
