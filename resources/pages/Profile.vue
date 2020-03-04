<template>
<div class="bg-teal-500">
	<div class="container mx-auto">
		<nav class="flex items-center justify-between flex-wrap p-6">
		 <div class="flex items-center flex-shrink-0 text-white mr-6">
		    <span class="font-semibold text-xl tracking-tight">GitHub Profile</span>
		  </div>
		  <div class="block lg:hidden">
		    <button class="flex items-center px-3 py-2 border rounded text-teal-200 border-teal-400 hover:text-white hover:border-white">
		      <svg class="fill-current h-3 w-3" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><title>Menu</title><path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"/></svg>
		    </button>
		  </div>
		  <div class="w-full block flex-grow md:flex md:items-center lg:w-auto md:w-auto">
		    <div class="text-sm lg:flex-grow">
		    </div>
		    <div>
		      <a href="#" class="inline-block text-sm px-4 py-2 leading-none border rounded text-white border-white hover:border-transparent hover:text-teal-500 hover:bg-white mt-4 lg:mt-0">Home</a>
		      <a href="#" class="inline-block text-sm px-4 py-2 leading-none border rounded text-white border-white hover:border-transparent hover:text-teal-500 hover:bg-white mt-4 lg:mt-0">GitHub</a>
		    </div>
			</div>
		</nav>
		<div>
			<div class="bg-white rounded-lg p-6">
			    <img class="h-16 w-16 md:h-24 md:w-24 rounded-full mx-auto md:mx-0 md:mr-6" :src="profileavatar_url">
			    <div class="text-center md:text-left">
			      <h2 class="text-lg">Erin Lindford</h2>
			      <div class="text-purple-500">Customer Support</div>
			      <div class="text-gray-600">erinlindford@example.com</div>
			      <div class="text-gray-600">(555) 765-4321</div>
			    </div>
			  </div>
		</div>
		{{ profile }} {{ getprofile() }}
	</div>
</div>
</template>

<script>
import GitHub from "github-api";
const gh = new GitHub();
export default {
	data () {
	    return { 
	    	user: [],
	    	profile:[]
	    }
	},
	asyncData: ({ req }) => ({
    	user: gh.getUser('jualahmed')
  	}),
  	methods:{
  		async getprofile(){
  			var self = this;
  			console.log(this.user);
	  		var profile = (await this.user.getProfile()).data;
	  		console.log(profile);
	  		self.profile=profile
	      	// repos = (await user.listRepos({ type: "owner" })).data.map(i => ({
	      	//   ...i,
	      	//   languageColor: langColors[i.language]
	      	// }));
  		}
  	}
};
</script>