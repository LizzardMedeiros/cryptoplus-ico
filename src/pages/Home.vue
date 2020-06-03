<template>
  <div id="home">
    <header-vue :language="language"/>
    <ico-status :language="language" :icoends="icoends"/>
    <solution-section :language="language"/>
    <token-section :language="language"/>
    <roadmap-section :language="language"/>
    <footer-vue :language="language"/>
  </div>
</template>

<script>

import HeaderVue from '@/components/header/HeaderVue';
import FooterVue from '@/components/footer/FooterVue';
import IcoStatus from '@/components/body/IcoStatus';
import SolutionSection from '@/components/body/SolutionSection';
import TokenSection from '@/components/body/TokenSection';
import RoadmapSection from '@/components/body/RoadmapSection';

export default {
  name: 'Home',
  components: {
    HeaderVue, FooterVue, IcoStatus, SolutionSection, TokenSection, RoadmapSection
  },
  methods:{
  },
  created: function(){
    let searchParams = new URLSearchParams(window.location.search);
    console.log(searchParams.has('lang'))
    if(searchParams.has('lang')) switch(searchParams.get('lang')){
      case "pt":
        this.language = "ptbr";
        break;
      case "en":
      default:
        this.language = "enus";
        break;
    } else {
      var userLang = navigator.language || navigator.userLanguage; 
      switch(userLang){
        case "pt-BR":
          this.language = "ptbr";
          break
        default:
          this.language = "enus";
        break;
      }
    }
  },
  data () {
    return{
      language: "ptbr",
      icoends: "05/12/2021 00:00:00"
    }
  }
}
</script>
  
<style>

  section{
    position:relative;
  }

  #home{
    font-family: 'Exo', sans-serif;
    background-color: black;
  }

  .icon-container{
    position: absolute;
  }

</style>
