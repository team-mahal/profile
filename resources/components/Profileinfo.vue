<template>
<div>
	<img class="border-8 border-blue-500 h-32 w-32 rounded-full mx-auto" :src="profile.avatar_url">
	<h2 class="text-lg text-black">{{ profile.name }}</h2>
	{{ profile }} 
</div>
</template>

<script>
import GitHub from "github-api";
const gh = new GitHub();
export default {
	props:['user'],
	data () {
	    return { 
	    	profile: [],
	    }
	},
	async created(){
		var user = gh.getUser('Synchro');
		this.profile = (await user.getProfile()).data;
	}
};
</script>