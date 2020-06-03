<template>
  <section id="ico" class="container white-text">
    <div class="row">
      <div class="col l6 m6 s12 center dancing">
        <img src="@/assets/1.png"/>
      </div>

      <div class="col l6 m6 s12">
        <div>
            <h5 class="center-align teal-text text-lighten-3">{{dictionary.our_numbers}}</h5>
            <div class="row center-align">
              <div class="col s4 center-align">
                  <h6>100000000 CRP</h6>
                  <label>{{dictionary.total_supply}}</label>
              </div>
              <div class="col s4 center-align">
                  <h6>0 CRP</h6>
                  <label>{{dictionary.burned}} CRP</label>
              </div>
              <div class="col s4 center-align">
                  <h6>0 CRP</h6>
                  <label>{{dictionary.total_shares}}</label>
              </div>
            </div>
            <hr class="teal-text text-lighten-3">
            <div class="row center-align">
              <div class="col s6 center-align">
                  <h6>R$ 0,00</h6>
                  <label>{{dictionary.raised}}</label>
              </div>
              <div class="col s6 center-align">
                  <h6>0 CRP</h6>
                  <label>{{dictionary.emited}}</label>
              </div>
            </div>          	
            <div>
              <div class="progress">
                <div class="determinate" style="width: 0%"></div>
              </div>
              <div class="row" style="margin: -20px;">
                <div class="col s6 push-s2 left-align"><i class="material-icons">keyboard_arrow_up</i> {{dictionary.soft_cap}}</div>
                <div class="col s6 pull-s2 right-align">{{dictionary.hard_cap}} <i class="material-icons">keyboard_arrow_up</i></div>
              </div>
            </div>
        </div>
        <div style="margin-top:84px;">
            <h5 class="center-align teal-text text-lighten-3">{{dictionary.ico_status}}</h5>
            <div class="center-align">
              <div>
                <label>{{dictionary.ico_starts}}:</label>
              </div>
              <div>
                <h6>{{days}} {{dictionary.days}} : {{hours}} {{dictionary.hours}} : {{minutes}} {{dictionary.minutes}} : {{seconds}} {{dictionary.seconds}}</h6>
              </div>
              <div>
                <a class="waves-effect waves-light btn-small" disabled>{{dictionary.btn_buy}}</a>
                <a class="waves-effect waves-light btn-small white black-text" disabled>{{dictionary.btn_sell}}</a>
              </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
name: 'IcoStatus',
created: function(){
    let lang = require(`@/json/lang/${this.language}.json`);
    this.dictionary = lang.ico;
  this.refreshDate();
  this.start();
},
props:["icoends", "language"],
methods:{
  refreshDate() {
    let now = new Date();
    let ends = new Date(this.icoends);
    let timestamp = ends.getTime() - now.getTime();
    let d = timestamp / (8.64 * Math.pow(10, 7));
    this.days = parseInt(d);
    let sub = (d - this.days)*24;
    this.hours = parseInt(sub);
    this.minutes = parseInt((sub * 60)%60);
    this.seconds = parseInt((sub * 60 * 60)%60);
  },
    start () {
        this.isRunning = true;
        let time = this.days + this.hours + this.minutes + this.seconds; 
        if (time) {
          this.timer = setInterval(() => {
              if (this.seconds == 0 && this.minutes > 0){
                  this.seconds = 59;
                  this.minutes--;
              } else if(this.seconds > 0) this.seconds--;

              if(this.minutes == 0 && this.hours > 0){
                  this.minutes = 59;
                  this.hours--;
              }

              if(this.hours == 0 && this.days > 0){
                  this.hours = 23;
                  this.days--;
              }

              if((this.days + this.hours + this.minutes + this.seconds) <= 0) clearInterval(this.timer);

          },1000);
        }
    }
},
data () {
    return{
      dictionary: null,
      timer: 0,
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0
    }
  }
}
</script>

<style>
#ico {
    background-color: black;
    margin-bottom: 0;
    scroll-behavior: smooth;
  }

  #ico hr{
    border-top: 0.5px solid;
    max-width: 15%;
  }

  #ico .dancing img{
    -webkit-animation: up-down 2s infinite alternate ease-in-out;
    animation: up-down 2s infinite alternate ease-in-out;
  }

@media (max-width: 600px){
    .s12 img{
      width: 256px;
    }
  }

@-webkit-keyframes up-down {
  0% { -webkit-transform: translateY(0) }
  100% { -webkit-transform: translateY(20px) }
}

@keyframes up-down{
  0% { 
        transform: translateY(0);
      }
  100% { 
        transform: translateY(20px);
      }
}
</style>