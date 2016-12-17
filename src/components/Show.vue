<template lang="html">
  <div>
    <div id="header">
      <span class="tital" @click="home">
        <img src="./Banner.png" class="banner" alt=""></span>
    </div>
    <div class="column">
      <h3 class="tital subtitle is-3"></h3>
    </div>
    <div class="column">
      <cards :list="list" v-for="list in lists" :score-sports="scoreSports" ></cards>
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
  }
}
</script>

<style lang="css">
</style>
