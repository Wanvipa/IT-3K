<template lang="html">
  <div class=""><br>
    <div  class ="width-card">
        <div v-show="list.sport === 'Badminton' || list.sport === 'Table Tennis' ||  list.sport === 'Volleyball'" class="card-content">
          <div class="media">
            <div class="media-content">
              <div class="tap">
                <p class="title is-5 textsport" >
                  <img src="./sport.png" class="tapstatus" alt="">: {{list.sport}} ( {{list.status}} )<br>
                  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<small class="sizedate">{{fromNow}}</small>
                </p>
              </div>
              </div>
          </div>
          <div class="content"><br>
            <h5 class="subtitle is-5 ">{{list.competition}}</h5>
            <div class="" v-for="score in scoreSports" v-if="score.sportId === list.id && score.status">SET {{score.set}}&nbsp; {{list.kind}}
              <h2 class="title is-2 textred ">{{score.team1}} - {{score.team2}}</h2>
              ( {{list.total1}} - {{list.total2}} )<br><br>
              <a :href="list.locationLink"><h5 class="subtitle is-5 texttype "><i class="fa fa-map-marker location" aria-hidden="true"></i> : {{list.location}}</a>
              </div>
            </div>
          </div>
          <div v-show="list.sport === 'Basketball'" class="card-content">
            <div class="media">
              <div class="media-content">
                <div class="tap">
                  <p class="title is-5 textsport" >
                    <img src="./sport.png" class="tapstatus" alt="">: {{list.sport}} ( {{list.status}} )<br>
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<small class="sizedate">{{fromNow}}</small>
                  </p>
                </div>
                </div>
            </div>
            <div class="content"><br>
              <h5 class="subtitle is-5 ">{{list.competition}}</h5>
              <div class="" v-for="score in scoreSports" v-if="score.sportId === list.id && score.status">ประเภท : {{list.kind}}
                <h2 class="title is-2 textred ">{{score.team1}} - {{score.team2}}</h2>
                
                <a :href="list.locationLink"><h5 class="subtitle is-5 texttype "><i class="fa fa-map-marker location" aria-hidden="true"></i> : {{list.location}}</a>
                </div>
              </div>
            </div>
            <div v-show="list.sport === 'Football'" class="card-content">
              <div class="media">
                <div class="media-content">
                  <div class="tap">
                    <p class="title is-5 textsport" >
                      <img src="./sport.png" class="tapstatus" alt="">: {{list.sport}} ( {{list.status}} )<br>
                      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<small class="sizedate">{{fromNow}}</small>
                    </p>
                  </div>
                  </div>
              </div>
              <div class="content"><br>
                <h5 class="subtitle is-5 ">{{list.competition}}</h5>
                <div class="" v-for="score in scoreSports" v-if="score.sportId === list.id && score.status">
                  <h2 class="title is-2 textred ">{{score.team1}} - {{score.team2}}</h2>
                  <a :href="list.locationLink"><h5 class="subtitle is-5 texttype "><i class="fa fa-map-marker location" aria-hidden="true"></i> : {{list.location}}</a>
                  </div>
                </div>
              </div>
        </div>
      </div>
</template>

<script>
/* global moment */
export default {
  props: ['list', 'scoreSports'],
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
