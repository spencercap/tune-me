<template>
    <div class="barContainer" :style="`height: ${h}px`"></div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'Bar',
    props: {
        h: {
            type: Number,
            required: true
        }
    },
	data() {
		return {
            hello: 'world',
            colors: {
                foreground: '#fff',
                background: '#4d4d4d'
            }
		}
	}
});
</script>

<style scoped>
.barContainer {
    background: #fff;

    width: 6px;
    height: 40px;
    border-radius: 2.7px;

    margin-right: 4.75px;

    transition: height .2s ease-out;
}
.barContainer:last-of-type {
    margin-right: 0;
}
</style>