<template>
	<img alt="Vue logo" src="./assets/logo.png" />
	<HelloWorld msg="Hello Vue 3.0 + Vite" />
</template>


<script lang="ts">
import { defineAsyncComponent, defineComponent } from 'vue';

export default defineComponent({
	name: 'App',
	components: {
		HelloWorld: defineAsyncComponent(() => import('./components/HelloWorld.vue'))
	},
	data() {
		return {
			hello: 'world'
		};
	}
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
}
</style>