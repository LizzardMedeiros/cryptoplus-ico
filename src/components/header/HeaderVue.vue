<template>
    <section id="header">
      <div class="bg-video">
        <video autoplay loop muted src="@/assets/blockchain_bg.mp4"></video>
      </div>
      <div class="content">
        <navbar-vue :language="language"/>
        <div class="center-align">
          <img class="logo" src="@/assets/logo.svg">
          <h4 class="white-text">{{dictionary.subtitle}}</h4>
          <a class="waves-effect waves-light btn-small white black-text" target="_blank" href="#">White Paper v.1.0</a>
          <a class="waves-effect waves-light btn-small" target="_blank" href="#" disabled>{{dictionary.btn_app}}</a>
        </div>
        <img src="@/assets/label.svg" style="width:100%; position:absolute; bottom:0;">
      </div>
    </section>
</template>

<script>
import NavbarVue from '@/components/navbar/NavbarVue';

export default {
  name: 'Header',
  components: {
    NavbarVue
  },
  props:['language'],
  created: function(){
    let lang = require(`@/json/lang/${this.language}.json`);
    this.dictionary = lang.header;
  },
  data(){
    return{
      dictionary: null
    }
  }
}
</script>

<style>
  #header{
    min-width: 100%;
    height: calc(100vh + 100px);
    width: auto;
    padding: 0;
  }

  #header video{
    position: absolute;
    right: 0;
    bottom: 0;
    min-width: 100%;
    min-height: 100%;
    width: auto;
    height: auto;
  }

  .content{
    position: relative;
    background: rgba(0, 0, 0, .5);
    height: 100%;
    width: auto;
  }

  .logo {
    width: 256px;
    margin: 80px 0 auto;
    -webkit-animation: sk-rotateplane 3s 1 ease-out;
    animation: sk-rotateplane 3s 1 ease-out;
  }

  @-webkit-keyframes sk-rotateplane {
    0% { -webkit-transform: perspective(256px) }
    100% { -webkit-transform: perspective(256px) rotateY(2160deg)}
  }

  @keyframes sk-rotateplane {
    0% { 
      transform: perspective(256px) rotateY(0deg);
      -webkit-transform: perspective(256px) rotateY(0deg) 
    }

    100% { 
      transform: perspective(256px) rotateY(-2160.9deg);
      -webkit-transform: perspective(256px) rotateY(-2160deg);
    }
  }

</style>