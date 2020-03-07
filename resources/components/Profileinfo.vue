<template>
<div class="text-center">
	<img class="border-8 border-blue-500 h-40 w-40 rounded-full mx-auto" :src="profile.avatar_url">
	<h2 class="text-xl text-black text-white text-4xl font-semibold">{{ profile.name }}</h2>
	<a class="block text-blue-900 text-2xl" :href="'https://github.com/'+profile.login" target="blank">@{{ profile.login }}</a>
	<div class="flex text justify-center">
		<p class="flex items-center">
			<svg aria-hidden="true"  data-prefix="fal" data-icon="map-marker" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512"
				class="h-5 w-5 svg-inline--fa fa-map-marker fa-w-12 fa-2x">
				<path fill="currentColor" d="M192 0C86 0 0 86 0 192c0 77 27 99 172 310 10 13 30 13 40 0 145-211 172-233 172-310C384 86 298 0 192 0zm0 474C53 272 32 256 32 192A159 159 0 01192 32a159 159 0 01160 160c0 64-21 80-160 282z"/>
			</svg>
			<span class="pl-2">{{ profile.location }}</span>
		</p>
		<p class="pl-3 flex items-center">
			<svg aria-hidden="true" data-prefix="fal" data-icon="calendar-alt" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" class="h-5 w-5 svg-inline--fa fa-calendar-alt fa-w-14 fa-2x">
				<path fill="currentColor" d="M400 64h-48V12c0-6.6-5.4-12-12-12h-8c-6.6 0-12 5.4-12 12v52H128V12c0-6.6-5.4-12-12-12h-8c-6.6 0-12 5.4-12 12v52H48C21.5 64 0 85.5 0 112v352c0 26.5 21.5 48 48 48h352c26.5 0 48-21.5 48-48V112c0-26.5-21.5-48-48-48zM48 96h352c8.8 0 16 7.2 16 16v48H32v-48c0-8.8 7.2-16 16-16zm352 384H48c-8.8 0-16-7.2-16-16V192h384v272c0 8.8-7.2 16-16 16zM148 320h-40c-6.6 0-12-5.4-12-12v-40c0-6.6 5.4-12 12-12h40c6.6 0 12 5.4 12 12v40c0 6.6-5.4 12-12 12zm96 0h-40c-6.6 0-12-5.4-12-12v-40c0-6.6 5.4-12 12-12h40c6.6 0 12 5.4 12 12v40c0 6.6-5.4 12-12 12zm96 0h-40c-6.6 0-12-5.4-12-12v-40c0-6.6 5.4-12 12-12h40c6.6 0 12 5.4 12 12v40c0 6.6-5.4 12-12 12zm-96 96h-40c-6.6 0-12-5.4-12-12v-40c0-6.6 5.4-12 12-12h40c6.6 0 12 5.4 12 12v40c0 6.6-5.4 12-12 12zm-96 0h-40c-6.6 0-12-5.4-12-12v-40c0-6.6 5.4-12 12-12h40c6.6 0 12 5.4 12 12v40c0 6.6-5.4 12-12 12zm192 0h-40c-6.6 0-12-5.4-12-12v-40c0-6.6 5.4-12 12-12h40c6.6 0 12 5.4 12 12v40c0 6.6-5.4 12-12 12z"/>
			</svg>
			<span class="pl-2">{{ profile.created_at }}</span>
		</p>
	</div>
	<div class="flex items-center justify-center">
		<div class="p-3 m-3 rounded-md text-white bg-gray-700">
			<p>{{ profile.public_repos }}</p>
			<p>Repositories</p>
		</div>
		<div class="p-3 m-3 rounded-md text-white bg-gray-700">
			<p>{{ profile.followers  }}</p>
			<p>Followers</p>
		</div>
		<div class="p-3 m-3 rounded-md text-white bg-gray-700">
			<p>{{ profile.following }}</p>
			<p>Following</p>
		</div>
	</div>
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