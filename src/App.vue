<template>
	<h3>
		<span>Scan w the Spotify app</span>
		<br />
		<span style="font-size: 0.8em">Find some music</span>
	</h3>

	<div
		v-if="hello"
		style="max-width: 300px; font-size: 13px; padding-bottom: 36px"
	>
		can we discover music by randomly generating Spotify codes? call it
		modern crate digging with a blindfold on. go try and find a code that
		can be scanned!
	</div>
	<!-- <HelloWorld msg="Hello Vue 3.0 + Vite" /> -->
	<SpotCode />
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
</style>
