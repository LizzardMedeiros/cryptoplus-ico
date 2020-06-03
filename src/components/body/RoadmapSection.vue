<template>
  <section id="roadmap">
    <div class="container">
      <h3>Roadmap</h3>
    </div>
    <ul class="timeline">
      <!-- Item 1 -->
      <li v-for="(item, i) in dictionary" :key="i">
        <div :class="'direction-'+item.direction">
          <div class="flag-wrapper">
            <span class="hexa"></span>
            <span class="flag">{{item.title}}</span>
            <span class="time-wrapper"><span class="time">{{item.time}}</span></span>
          </div>
          <ul class="desc collapsible popout">
            <li>
              <div class="collapsible-header">
                <i class="material-icons">{{item.icon}}</i>{{item.subtitle}}
                <label><i class="material-icons">more_vert</i></label>
              </div>
              <div class="collapsible-body">
                <span v-for="(topic, i) in item.topics" :key="i">
                  <p>{{topic[0]}}
                    <label class="material-icons" v-if="topic[1]">done</label>
                  </p>                   
                </span>
              </div>
            </li>
          </ul>
        </div>
      </li>
    </ul>
  </section>
</template>

<script>
import M from 'materialize-css'

export default {
  name: 'RoadmapSection',
  props:['language'],
  components: {
  },
  created: function(){
    let lang = require(`@/json/lang/${this.language}.json`);
    this.dictionary = lang.roadmap;
  },
  mounted: function(){
    let elems = document.querySelectorAll('.collapsible');
    M.Collapsible.init(elems, {});
  },
  data () {
    return{
      dictionary: null
    }
  }
}
</script>
  
<style>

  #roadmap{
    background-color: white;
    padding-top: 0;
  }

  #roadmap .hexa{
    border: 0px;
    float: left;
    text-align: center;
    height: 35px;
    width: 60px;
    font-size: 22px;
    background: #f0f0f0;
    color: #3c3c3c;
    position: relative;
    margin-top: 15px;
  }

  #roadmap .hexa:before{
    content: ""; 
    position: absolute; 
    left: 0; 
    width: 0; 
    height: 0;
    border-bottom: 15px solid #f0f0f0;
    border-left: 30px solid transparent;
    border-right: 30px solid transparent;
    top: -15px;
  }

  #roadmap .hexa:after{
    content: ""; 
    position: absolute; 
    left: 0; 
    width: 0; 
    height: 0;
    border-left: 30px solid transparent;
    border-right: 30px solid transparent;
    border-top: 15px solid #f0f0f0;
    bottom: -15px;
  }

  #roadmap .timeline {
    position: relative;
    padding: 0;
    width: 100%;
    margin-top: 20px;
    list-style-type: none;
  }

  #roadmap .timeline:before {
    position: absolute;
    left: 50%;
    top: 0;
    content: ' ';
    display: block;
    width: 2px;
    height: 100%;
    margin-left: -1px;
    background: rgb(213,213,213);
    background: -moz-linear-gradient(top, rgba(213,213,213,0) 0%, rgb(213,213,213) 8%, rgb(213,213,213) 92%, rgba(213,213,213,0) 100%);
    background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,rgba(30,87,153,1)), color-stop(100%,rgba(125,185,232,1)));
    background: -webkit-linear-gradient(top, rgba(213,213,213,0) 0%, rgb(213,213,213) 8%, rgb(213,213,213) 92%, rgba(213,213,213,0) 100%);
    background: -o-linear-gradient(top, rgba(213,213,213,0) 0%, rgb(213,213,213) 8%, rgb(213,213,213) 92%, rgba(213,213,213,0) 100%);
    background: -ms-linear-gradient(top, rgba(213,213,213,0) 0%, rgb(213,213,213) 8%, rgb(213,213,213) 92%, rgba(213,213,213,0) 100%);
    background: linear-gradient(to bottom, rgba(213,213,213,0) 0%, rgb(213,213,213) 8%, rgb(213,213,213) 92%, rgba(213,213,213,0) 100%);
    z-index: 5;
  }

  #roadmap .timeline li {
    padding: 2em 0;
  }

  #roadmap .timeline .hexa{
    width: 16px;
    height: 10px;
    position: absolute;
    background: #0d4043;
    z-index: 5;
    left: 0;
    right: 0;
    margin-left:auto;
    margin-right:auto;
    top: -30px;
    margin-top: 0;
  }

  #roadmap .timeline .hexa:before {
    border-bottom: 4px solid #0d4043;
    border-left-width: 8px;
    border-right-width: 8px;
    top: -4px;
  }

  #roadmap .timeline .hexa:after {
    border-left-width: 8px;
    border-right-width: 8px;
    border-top: 4px solid #0d4043;
    bottom: -4px;
  }

  #roadmap .direction-l,
  #roadmap .direction-r {
    float: none;
    width: 100%;
    text-align: center;
  }

  #roadmap .flag-wrapper {
    text-align: center;
    position: relative;
  }

  #roadmap .flag {
    position: relative;
    display: inline;
    background: rgb(255,255,255);
    font-weight: 600;
    z-index: 15;
    padding: 6px 10px;
    text-align: left;
    border-radius: 5px;
  }

  #roadmap .direction-l .flag:after,
  #roadmap .direction-r .flag:after {
    content: "";
    position: absolute;
    left: 50%;
    top: -15px;
    height: 0;
    width: 0;
    margin-left: -8px;
    border: solid transparent;
    border-bottom-color: rgb(255,255,255);
    border-width: 8px;
    pointer-events: none;
  }

  #roadmap .direction-l .flag {
    -webkit-box-shadow: -1px 1px 1px rgba(0,0,0,0.15), 0 0 1px rgba(0,0,0,0.15);
    -moz-box-shadow: -1px 1px 1px rgba(0,0,0,0.15), 0 0 1px rgba(0,0,0,0.15);
    box-shadow: -1px 1px 1px rgba(0,0,0,0.15), 0 0 1px rgba(0,0,0,0.15);
  }

  #roadmap .direction-r .flag {
    -webkit-box-shadow: 1px 1px 1px rgba(0,0,0,0.15), 0 0 1px rgba(0,0,0,0.15);
    -moz-box-shadow: 1px 1px 1px rgba(0,0,0,0.15), 0 0 1px rgba(0,0,0,0.15);
    box-shadow: 1px 1px 1px rgba(0,0,0,0.15), 0 0 1px rgba(0,0,0,0.15);
  }

  #roadmap .time-wrapper {
    display: block;
    position: relative;
    margin: 4px 0 0 0;
    z-index: 14;
    line-height: 1em;
    color: #fff;
  }

  #roadmap .direction-l .time-wrapper {
    float: none;
  }

  #roadmap .direction-r .time-wrapper {
    float: none;
  }

  #roadmap .time {
    background: #0d4043;
    display: inline-block;
    padding: 8px;
  }

  #roadmap .desc {
    position: relative;
    margin: 1em 0 0 0;
    padding: 1em;
    background: rgb(254,254,254);
    z-index: 15;
  }

  #roadmap .direction-l .desc,
  #roadmap .direction-r .desc {
    position: relative;
    margin: 1em 1em 0 1em;
    padding: 0;
    z-index: 15;
  }

  @media(min-width: 768px){
    #roadmap .timeline {
      width: 660px;
      margin: 0 auto;
      margin-top: 20px;
    }

    #roadmap .timeline li:after {
      content: "";
      display: block;
      height: 0;
      clear: both;
      visibility: hidden;
    }
    
    #roadmap .timeline .hexa {
      left: -28px;
      right: auto;
      top: 8px;
    }

    #roadmap .timeline .direction-l .hexa {
      left: auto;
      right: -28px;
    }

    #roadmap .direction-l {
      position: relative;
      width: 310px;
      float: left;
      text-align: right;
    }

    #roadmap .direction-r {
      position: relative;
      width: 310px;
      float: right;
      text-align: left;
    }

    #roadmap .flag-wrapper {
      display: inline-block;
    }
    
    #roadmap .flag {
      font-size: 18px;
    }

    #roadmap .direction-l .flag:after {
      left: auto;
      right: -16px;
      top: 50%;
      margin-top: -8px;
      border: solid transparent;
      border-left-color: rgb(254,254,254);
      border-width: 8px;
    }

    #roadmap .direction-r .flag:after {
      top: 50%;
      margin-top: -8px;
      border: solid transparent;
      border-right-color: rgb(254,254,254);
      border-width: 8px;
      left: -8px;
    }

    #roadmap .time-wrapper {
      display: inline;
      vertical-align: middle;
      margin: 0;
    }

    #roadmap .direction-l .time-wrapper {
      float: left;
    }

    #roadmap .direction-r .time-wrapper {
      float: right;
    }

    #roadmap .time {
      padding: 5px 10px;
    }

    #roadmap .direction-r .desc {
      margin: 1em 0 0 0.75em;
    }
  }

  @media(min-width: 992px){
    #roadmap .timeline {
      width: 800px;
      margin: 0 auto;
      margin-top: 20px;
    }

    #roadmap .direction-l {
      position: relative;
      width: 380px;
      float: left;
      text-align: right;
    }

    #roadmap .direction-r {
      position: relative;
      width: 380px;
      float: right;
      text-align: left;
    }
  }

</style>
