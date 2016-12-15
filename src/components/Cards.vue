<template lang="html">
  <!-- Sport -->
  <div class="app" >
  <div  class ="width-card"v-show="list.type==='sport'">
      <div class="card-content">
        <div class="media">
          <div class="media-content">
            <div class="tap">
              <p class="title is-5 texttype" >
                <i class="fa fa-futbol-o " aria-hidden="true"></i>
                &nbsp;{{list.sport}} ( {{list.status}} )<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<small>{{fromNow}}</small>
              </p>
            </div>
            </div>
        </div>
        <div class="content"><br>
          <h5 class="subtitle is-5 ">{{list.competition}}</h5>
          <div class="" v-for="score in scoreSports" v-show="score.sportId === list.id && score.status">SET {{score.set}}&nbsp; {{list.kind}}
            <h2 class="title is-2 textred ">{{score.team1}} - {{score.team2}}</h2>
            ( {{list.total1}} - {{list.total2}} )<br><br>
            <a :href="list.locationLink"><h5 class="subtitle is-5 texttype ">location : {{list.location}}</a><br><br>
              <img :src="list.map" width="600" alt="" v-show="map">
            </div>
          </div>
        </div>
      </div>

      <!-- ส่วนของกิจกรรมต่างๆ -->
      <div  class ="width-card"v-show="list.type==='Program'">
        <div class="card-content">
          <div class="media">
            <div class="media-content">
              <div class="tap">
                <p class="title is-5 texttype">
                  <img src="./event.png" alt="">
              </div>
            </div>
          </div>
          <div class="content "><br>
            <h5 class="subtitle is-5 ">{{list.message}}<br></h5>
            <a :href="list.locationLink"><h5 class="subtitle is-5 ">สถานที่ : {{list.location}}</a>
            <small class="sizedate">{{list.time}}</small><small>{{fromNow}}</small>
          </p>
          </div>
        </div>
      </div>

      <!-- รูปภาพ -->
      <div  class ="width-card"v-show="list.type==='Picture'">
        <div class="card-image">
          <figure class="image is-3by2">
            <img :src="list.picture" alt="">
          </figure>
        </div>
        <div class="card-content">
          <div class="media">
            <div class="media-content">
              <div class="tap">
                <img src="./photo.png" class="tapstatus" alt="">
              </div>
          </div>
        </div>
        <div class="content "><br>
          <h5 class="subtitle is-5 font-th">{{list.caption}}<br></h5>
          <small class="sizedate">{{list.time}}</small>
        </div>
      </div>
    </div>
    <div>
    </template>

<script>
/* global moment */
export default {
  props: ['list', 'scoreSports'],
  data () {
    return {
      map: false,
      timestamp: moment(this.list.time),
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
