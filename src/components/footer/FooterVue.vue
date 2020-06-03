<template>
  <footer class="page-footer grey darken-4" id="contacts">
    <div class="container">
      <div class="row">
        <div class="col m6 s12">
            <div class="row valign-wrapper">
              <div class="col s3">
                <img src="@/assets/logo.svg" class="logo-img right" style=""/>
              </div>
              <div class="col s9">
                <h5 class="left"><span class="brand-text">CRYPTO<span style="color: #95F4F1;">PLUS</span></span></h5>
                <label>Token</label>
              </div>
            </div>
            <p>{{dictionary.subtitle}}</p>
        </div>
        <div class="col m3 s12">
          <h5 class="white-text">{{dictionary.contacts.title}}</h5>
          <ul>
            <li v-for="contacts in dictionary.contacts.list">
              <a class="grey-text text-lighten-3" :href="contacts[2]" target="_blank">
                <i :class="contacts[1]"></i> {{contacts[0]}}
              </a>
            </li>
          </ul>
        </div>
        <div class="col m3 s12">
          <h5 class="white-text">{{dictionary.links.title}}</h5>
          <ul>
            <li v-for="links in dictionary.links.list">
              <a class="grey-text text-lighten-3" :href="links[1]" target="_blank">
                {{links[0]}}
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <div class="footer-copyright grey darken-3">
      <div class="container center">
      © 2020 Copyright - By <a class="grey-text text-lighten-3" href="https://github.com/LizzardMedeiros/" target="_blank">LizzardMedeiros</a>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  props:['language'],
  created: function(){
    let lang = require(`@/json/lang/${this.language}.json`);
    this.dictionary = lang.footer;    
  },
  components: {
  },
  data(){
    return{
      dictionary: null
    }
  }
}
</script>

<style>
  a{
    color: white;
  }
  .logo-img{
    max-width: 42px;
    vertical-align: middle;
  }
</style>