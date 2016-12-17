<template lang="html">
  <div class="">
    <br>
  <div  class ="width-card">
    <div class="card-content">
      <div class="media">
        <div class="media-content">
          <img src="./event.png" class="tapstatus" alt=""><br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<small class="sizedate">{{fromNow}}</small>
        </div>
      </div>
      <div class="content "><br>
        <h5 class="subtitle is-5 ">{{list.message}}<br></h5>
        <a :href="list.locationLink"><h5 class="subtitle is-5 "><i class="fa fa-map-marker location" aria-hidden="true"></i> : {{list.location}}</a>
          {{date}}
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
    date () {
      return this.list.time.substr(10, this.list.time.length - 13) + ' - ' + this.list.endTime
    },
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
