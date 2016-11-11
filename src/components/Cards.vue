<template lang="html">
  <!-- Sport -->
  <div class="app" >
    <div  class ="width-card"v-show="list.type==='sport'">
      <div class="card-content">
        <div class="media">
          <div class="media-content">
              <p class="title is-5 ">
                <i class="fa fa-futbol-o " aria-hidden="true"></i>
                &nbsp;<text-type1>{{list.sport}} ( {{list.status}} )</text-type1><br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<small>{{timeout}}</small>
              </p>
            </div>
        </div>
        <div class="content"><br>
          <h5 class="subtitle is-5 ">{{list.competition}}</h5>
          <div class="" v-for="score in scoreSports" v-show="score.sportId === list.id && score.status">SET {{score.set}}&nbsp;( {{list.kind}} )
            <h2 class="title is-2 textred ">{{score.team1}} - {{score.team2}}</h2>
            ( {{list.total1}} - {{list.total2}} )<br><br>
            <h5 class="subtitle is-6 ">location : {{list.location}}<br><br>
              <small class="sizedate">{{list.time}}</small>
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
                <p class="title is-5">
                  <i class="fa fa-list-alt" aria-hidden="true"></i>
                  &nbsp;<text-type1>{{list.type}}</text-type1><br>
                  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<small>{{timeout}}</small>
                </p>
              </div>
            </div>
          </div>
          <div class="content "><br>
            <h5 class="subtitle is-5 ">{{list.message}}<br></h5>
            <h5 class="subtitle is-6 ">location : {{list.location}}<br><br>
            <small class="sizedate">{{list.time}}</small>
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
                <p class="title is-5 text textblack">
                  <i class="fa fa-picture-o" aria-hidden="true"></i>
                  &nbsp;<text-type1>{{list.type}}<br></text-type1>
                  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<small>{{timeout}}</small>
              </p>
            </div>
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
export default {
  props: ['list', 'scoreSports'],
  data () {
    return {
    }
  },
  computed: {
    timeout () {
      var time = ''
      if (this.list.timePost) {
        var timePost = this.list.timePost.split(':')
        var timeAgo = parseInt(timePost[0]) * 60 + parseInt(timePost[1])
        var today = new Date()
        var timeNow = today.getHours() * 60 + today.getMinutes()
        if (timeAgo === timeNow) {
          time = ' เมื่อสักครู่นี้'
        } else {
          if (timeNow - timeAgo < 60) {
            time = (timeNow - timeAgo) + 'นาทีที่แล้ว'
          } else {
            time = (parseInt(timeNow / 60) - parseInt(timeAgo / 60)) + 'ชั่วโมงที่แล้ว'
          }
        }
      }
      return time
    }
  },
  mounted () {
  },
  methods: {
  },
  components: {
  }
}
</script>

<style lang="css">
.app {
  margin-bottom: 20px;
}

.width-card {
  width: 100%;
  text-align: center;
  background-color: #fff;
  /*border-top:1px solid #EFEFEF;*/
  /*border-color: #ccff90;*/
}

.textred{
  color: #d32f2f !important;
}
.textstatus{
  color: #42B72A;
}
.sizedate{
  font-size: 13px !important;
  margin-top: auto;
}



</style>
