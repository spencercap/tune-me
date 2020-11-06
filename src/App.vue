<template>
	<h3>
		<span>Scan w the Spotify app</span>
		<br />
		<span style="font-size: 0.8em">Find some music</span>
	</h3>

	<!-- <HelloWorld msg="Hello Vue 3.0 + Vite" /> -->
	<SpotCode />

	<div
		v-if="hello"
		style="max-width: 300px; font-size: 13px; padding: 36px 0"
	>
		discover music from randomly generated Spotify codes - call it modern
		crate digging.
		<br />
		<br />
		<span style="font-size: 2em">🤷🏽‍♂️</span>
	</div>

	<div class="by">
		<span>✏️ &nbsp;</span>
		<a href="https://github.com/spencercap/tune-me" target="_blank"
			>@spencercap
		</a>
	</div>
</template>

<script lang="ts">
import { defineAsyncComponent, defineComponent } from 'vue';
import x from './components/HelloWorld.vue';

export default defineComponent({
	name: 'App',
	components: {
		HelloWorld: defineAsyncComponent(
			() => import('./components/HelloWorld.vue')
		),
		SpotCode: defineAsyncComponent(
			() => import('./components/SpotCode.vue')
		),
	},
	data() {
		return {
			hello: 'world',
		};
	},
});
</script>

<style>
#app {
	/* font-family: 'Benton Sans', Helvetica, Sans-serif; */
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;

	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
}

.by {
	position: fixed;
	bottom: 0;
	right: 0;
	margin: 0.5em 1em;
	font-size: 12px;
}
</style>
