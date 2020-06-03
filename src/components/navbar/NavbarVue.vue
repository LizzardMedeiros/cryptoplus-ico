<template>
	<nav class="navbar transparent">

		<!-- Dropdown Structure -->
		<ul id="dropdown1" class="dropdown-content">
		  <li><a href="?lang=en"><img src="@/assets/icons/usaflag.png" style="width: 32px;"></a></li>
		  <li><a href="?lang=pt"><img src="@/assets/icons/brflag.png" style="width: 32px;"></a></li>
		</ul>

		<div class="row nav-container">

			<div class="brand-container col s6 m4 left-align">
			    <img src="@/assets/logo.svg" class="hide-on-med-and-down" />
			    <div class="brand-text">Crypto<span style="color: #95F4F1;">PLUS</span></div>
			</div>

			<div class="links-container col s6 m8">
				<ul class="nav-mobile right">
					<span class="hide-on-med-and-down">
						<li><a href="#ico">{{dictionary.ico}}</a></li>
						<li><a href="#solution">{{dictionary.solutions}}</a></li>
						<li><a href="#token">{{dictionary.our_token}}</a></li>
						<li><a href="#roadmap">{{dictionary.roadmap}}</a></li>
						<li><a href="#contacts">{{dictionary.contacts}}</a></li>
					</span>
					<li>
					   	<a class="dropdown-trigger" href="#" data-target="dropdown1">
					   		<img :src="getFlagImage()"/>
					   	</a>
				   	</li>
				</ul>
			</div>

		</div>
	</nav>
</template>

<script>
export default {
  name: 'NavbarVue',
  props:["language"],
  mounted: function () {
  	$(".dropdown-trigger").dropdown();
  },
  created: function(){
  	let lang = require(`@/json/lang/${this.language}.json`);
    this.dictionary = lang.navbar;
  },
  methods:{
  	getFlagImage(){
  		var pic = "";
		switch(this.language){
		    case "ptbr":
		    	pic = "brflag.png";
		        break;
		    case "enus":
		      default:
		        pic = "usaflag.png";
		        break;
	    }
  		return require(`@/assets/icons/${pic}`)
  	}
  },
  data(){
  	return{
  		dictionary: null
  	}
  }
}
</script>

<style>

	nav {
		height: 64px;
	}

	.nav-container {
		width: 100%;
		display: flex;
		justify-content: space-between;
		padding: 0 32px;
	}

	.brand-container, .links-container {
		display: flex;
		align-items: center;
	}

	.brand-container {
		justify-content: flex-start;
	}

	.links-container {
		justify-content: flex-end;
	}

	.brand-container img{
	    width: 42px;
	}

	.dropdown-trigger {
		display: flex;
		height: 64px;
		align-items: center;
	}

	.dropdown-trigger img{
		width: 32px;
	}

	.brand-container .brand-text {
		font-size: 24px;
		letter-spacing: 4px;
		text-transform: uppercase;
		margin-left: 8px;
	}
</style>
