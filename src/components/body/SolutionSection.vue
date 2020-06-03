<template>
<section id="solution" class="white-text">
  <div class="row container">
    <div class="col s12 center">
      <div class="row">

        <div class="col m5 s12">
          <div><h5 class="teal-text text-lighten-3">{{dictionary.the_issue[0]}}</h5></div>
          <div>{{dictionary.the_issue[1]}}</div>
        </div>

        <div class="col m2 s12">
          <span class="between-cols btn-floating btn hide-on-small-only show-on-medium-and-up teal pulse center"><i class="material-icons">arrow_forward</i></span>
          <span class="between-cols btn-floating btn hide-on-med-and-up show-on-small teal pulse center"><i class="material-icons">arrow_downward</i></span>
      </div>

        <div class="col m5 s12">
          <div><h5 class="teal-text text-lighten-3">{{dictionary.our_solution[0]}}</h5></div>
          <div>{{dictionary.our_solution[1]}}</div>
        </div>

      </div>

      <div class="row center-align">
        <div class="col m4 s12">
          <div><h6 class="teal-text text-lighten-2"><i class="material-icons">insert_chart</i> {{dictionary.profit_holding[0]}}</h6></div>
          <div class="left-align">{{dictionary.profit_holding[1]}}</div>
        </div>
        <div class="col m4 s12">
          <div><h6 class="teal-text text-lighten-2"><i class="material-icons">verified_user</i> {{dictionary.trading_security[0]}}</h6></div>
          <div class="left-align">{{dictionary.trading_security[1]}}</div>
        </div>
        <div class="col m4 s12">
          <div><h6 class="teal-text text-lighten-2"><i class="material-icons">accessible</i> {{dictionary.ico_system[0]}}</h6></div>
          <div class="left-align">{{dictionary.ico_system[1]}}</div>
        </div>
      </div>
    </div>
  </div>
  </section>
</template>

<script>
import Lang from "@/json/lang/enus.json"
export default {
name: 'SolutionSection',
props:["language"],
created:function(){
    let lang = require(`@/json/lang/${this.language}.json`);
    this.dictionary = lang.solution;
},
data(){
  return{
    dictionary: Lang.solution
  }
}
}
</script>

<style>
.between-cols{
  position: absolute;
  top: 30%;
  left: 50%;
  transform: translate(-50%, -50%);
}
@media (max-width: 600px){
  .between-cols{
    top: 22%;
  }
  .s12{
    margin: 12px 0;
  }
}
</style>
