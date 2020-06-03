<template>
  <section id="token" style="margin-bottom: -30px">
    <img src="@/assets/label-mirror.svg" style="width:100%;"/>
    <div class="row container" style="padding-bottom: 0;">
      <div class="col m12">
        <div class="white-text"><h3>{{dictionary.title}}</h3></div>
        <img :src="getImgUrl(dictionary.scheme_image)" style="width: 100%; padding-bottom:150px;"/>
      </div>
      <div class="col m12">
        <img src="@/assets/label2.svg" style="position:absolute; width:100%; left:0; bottom:0">
      </div>
    </div>
  </section>
</template>

<script>

export default {
  name: 'TokenSection',
  components: {
  },
  methods:{
    getImgUrl(pic) {
      return require(`@/assets/${pic}`)
    }
  },
  props:["language"],
  created: function(){
      let lang = require(`@/json/lang/${this.language}.json`);
      this.dictionary = lang.token;
  },
  data () {
    return{
      dictionary: null
    }
  }
}
</script>
  
<style>

  #token{
    background-color: rgb(21,21,21);
    background-image: url("~@/assets/bg.jpg");
    background-attachment: fixed;
  }

</style>
