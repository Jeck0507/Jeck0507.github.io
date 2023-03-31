<template>


  <div class="black-bg" v-if="modal == true">
      <div class="white-bg">
        <h4>참여하는 인원수를 입력해주세요</h4>
        <input type="text" v-model="number" @keyup.enter="$event =>modal = false">
      </div>
  </div>




  <div class="header">


    <div class="title">
      <h4 class="main-title">TeamPorter</h4>
      <p class="sub-title">내전용 팀 짜주는 사이트</p>
    </div>


    <div  class="player-input">

      <input type="text" v-model="text" @keyup.enter="$event =>name_input()"><br>
      <button class="input-complited" @click="$event =>name_input_end()">입력 완료</button>

      <div class="mark-up">
       <p>입력된 사람 : {{markup_name}}	</p>
       <p>참여하는 사람 수 : {{number}}	</p>
       <p>**팀 나누기 버튼을 누르면 입력된 사람들이 섞입니다**</p>
     </div>


    </div>


    <button class="team-maing-button" @click="$event =>random_team()">팀 나누기</button>


    <div class="Team-markup">
      <p class="Team-A">Team A : {{ Div_TeamA }}</p>
      <p class="Team-B">Team B : {{ Div_TeamB }}</p>
    </div>

  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return{
      name : [],
      Div_TeamA : [],
      Div_TeamB : [],
      text:'',
      modal : true,
      number : '',
      input_possible : "입력",
      markup_name : []
    }
  },
  components: {
  },
  methods: {
    /** 이름 입력 */
    name_input(){
      if(this.input_possible == "입력"){
        for(let i = 0; i <=this.number; i++){
        if(this.text != ''){
          this.markup_name.push(this.text)
          this.name.push(this.text)
          this.text = ''
        }
        this.input_possible == "입력이 완료되었습니다"
        }
      }
    },
/**팀 만들기 */
    random_team() {
      var players = this.name;
      var amount = this.number;
      var gameScale = parseInt(amount / 2);
      
      
      players.sort(function() {
      return 0.5 - Math.random();
      });
      
      var TeamA = players.slice(0, gameScale);
      var TeamB = players.slice(gameScale);
      this.Div_TeamA = TeamA;
      this.Div_TeamB = TeamB;
    },
    name_input_end() {
      this.input_possible = "입력이 완료되었습니다";
    },
  },

}


</script>

<style>


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.main-title {
  font-size: 44px;
  margin-bottom: 10px;
}
body {
 margin : 0;
}
div {
 box-sizing: border-box;
}
.black-bg {
 width: 100%; height:100%;
 background: rgba(0,0,0,0.5);
 position: fixed; padding: 20px;
}
.white-bg {
 width: 100%; background: white;
 border-radius: 8px;
 padding: 20px;
} 

.player-input{
 background-color: wheat;
 padding: 10px;
 margin-bottom: 10px;
 margin-left: 400px;
 margin-right: 400px;
 border-radius: 10px;
 font-size: 20PX;
 box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
}

.input-complited{
 padding: 10px 20px;
 border-radius: 15px;
 margin: 10px;
 box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
 text-decoration: none;
 font-weight: 600;
 transition: 0.25s;
}

input {
 width:200px;
 height:40px;
 font-size:20px;
}

.Team-A{
 margin: 100px;
 background-color: rgb(243, 188, 166);
 padding: 10px;
 margin-bottom: 10px;
 margin-left: 400px;
 margin-right: 400px;
 border-radius: 10px;
 font-size: 30PX;
 box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
}

.Team-B{
 margin-top: 40px;

 background-color: rgb(119, 156, 255);
 padding: 10px;
 margin-bottom: 10px;
 margin-left: 400px;
 margin-right: 400px;
 border-radius: 10px;
 font-size: 30PX;
 box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
}

.team-maing-button{
 padding: 10px 10px;
 border-radius: 15px;
 margin: 10px;
 box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
 text-decoration: none;
 font-weight: 600;
 transition: 0.25s;
}
</style>