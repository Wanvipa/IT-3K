<template>
  <div class="body"  >
    <show :lists="lists" :score-sports="scoreSports"></show>
  </div>
</template>

<script>
import firebase from 'firebase'
var config = {
  apiKey: 'AIzaSyBasyXEYg3xGN6Y9ndOtt9chPV4m60_6Xw',
  authDomain: 'it-3k-1f766.firebaseapp.com',
  databaseURL: 'https://it-3k-1f766.firebaseio.com',
  storageBucket: 'it-3k-1f766.appspot.com',
  messagingSenderId: '914467199924'
}
firebase.initializeApp(config)
var It3k = firebase.database().ref('It3k')
var ScoreSports = firebase.database().ref('ScoreSports')
import Show from './components/Show'
export default {
  components: {
    Show
  },
  data () {
    return {
      lists: [],
      scoreSports: []
    }
  },
  mounted () {
    var vm = this
    It3k.on('child_added', function (snapshot) {
      var item = snapshot.val()
      item.id = snapshot.key
      vm.lists.splice(0, 0, item)
    })
    It3k.on('child_removed', function (snapshot) {
      var id = snapshot.key
      var index = vm.lists.findIndex(lists => lists.id === id)
      vm.lists.splice(index, 1)
    })
    It3k.on('child_changed', function (snapshot) {
      if (snapshot.val().type === 'sport') {
        var id = snapshot.key
        var item = snapshot.val()
        var sport = vm.lists.find(item => item.id === id)
        sport.type = item.type
        sport.time = item.time
        sport.kind = item.kind
        sport.competition = item.competition
        sport.location = item.location
        sport.status = item.status
        sport.sport = item.sport
        sport.total1 = item.total1
        sport.total2 = item.total2
        sport.map = item.map
      }
    })
    ScoreSports.on('child_added', function (snapshot) {
      var item = snapshot.val()
      item.id = snapshot.key
      vm.scoreSports.push(item)
    })
    ScoreSports.on('child_changed', function (snapshot) {
      var id = snapshot.key
      var item = snapshot.val()
      var scoreSport = vm.scoreSports.find(item => item.id === id)
      scoreSport.set = item.set
      scoreSport.sportId = item.sportId
      scoreSport.team1 = item.team1
      scoreSport.team2 = item.team2
      scoreSport.status = item.status
    })
  },
  methods: {}
}
</script>
<style lang="css">
@import url('https://fonts.googleapis.com/css?family=Kanit&subset=thai');
body{
  background-color:#f5f5f5;
  font-family: 'Kanit', sans-serif;
}

</style>
