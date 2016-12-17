<template lang="html">
  <div class="app">
    <br>
      <div  class ="width-card">
        <div class="card-image">
          <figure class="image is-3by2">
            <img :src="list.picture" alt="">
          </figure>
        </div>
        <div class="card-content">
          <div class="media">
            <div class="media-content">
              <img src="./photo.png" class="tapstatus" alt="">
            </div>
          </div>
          <div class="content "><br>
            <h5 class="subtitle is-5 ">{{list.caption}}<br></h5>
            <small class="sizedate">{{list.time}}</small>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
/* global moment */
export default {
  props: ['list'],
  data () {
    return {
      map: false,
      timestamp: '',
      count: 0
    }
  },
  created () {
    let vm = this
    setInterval(() => {
      vm.count++
    }, 1000)
  },
  computed: {
    fromNow () {
      this.count
      this.timestamp = moment(this.list.time)
      return moment(this.timestamp).fromNow()
    }
  },
  mounted () {
    moment.lang('th')
  },
  methods: {
  },
  components: {
  }
}
</script>


<style lang="css">
</style>
