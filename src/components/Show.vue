<template lang="html">
  <div>
      <div id="header">
        <span class="tital" @click="home">
        <i class="fa fa-home"></i><img src="./Banner.png" class="banner" alt=""></span>
        <!-- <h6 class="subtitle is-6">&nbsp;IT3K'14th : Once Upon A Time</h6> -->
      </div>

    <div class="column">
      <h3 class="tital subtitle is-3"></h3>
      </div>
      <div class="column" v-show="!inputData">
      <cards :list="list"  v-for="list in lists" :score-sports="scoreSports" ></cards>
      </div>
    <div class="column"></div>
  </div>

</template>
<script>
import Cards from './Cards'
export default {
  props: ['lists', 'scoreSports'],
  data () {
    return {
      inputData: false
    }
  },
  computed: {},
  mounted () {},
  methods: {
    home () {
      window.scrollTo(0, 0)
    }
  },
  components: {
    Cards
    // fromInput
  }
}
</script>

<style lang="css">
</style>
