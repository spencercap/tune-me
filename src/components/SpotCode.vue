<template>
    <div class="spotCodeContainer">
        <div class="spotifyLogo">
            <svg xmlns="http://www.w3.org/2000/svg" height="100%" width="100%" version="1.1" viewBox="0 0 168 168">
                <path :fill="colors.foreground" d="m83.996 0.277c-46.249 0-83.743 37.493-83.743 83.742 0 46.251 37.494 83.741 83.743 83.741 46.254 0 83.744-37.49 83.744-83.741 0-46.246-37.49-83.738-83.745-83.738l0.001-0.004zm38.404 120.78c-1.5 2.46-4.72 3.24-7.18 1.73-19.662-12.01-44.414-14.73-73.564-8.07-2.809 0.64-5.609-1.12-6.249-3.93-0.643-2.81 1.11-5.61 3.926-6.25 31.9-7.291 59.263-4.15 81.337 9.34 2.46 1.51 3.24 4.72 1.73 7.18zm10.25-22.805c-1.89 3.075-5.91 4.045-8.98 2.155-22.51-13.839-56.823-17.846-83.448-9.764-3.453 1.043-7.1-0.903-8.148-4.35-1.04-3.453 0.907-7.093 4.354-8.143 30.413-9.228 68.222-4.758 94.072 11.127 3.07 1.89 4.04 5.91 2.15 8.976v-0.001zm0.88-23.744c-26.99-16.031-71.52-17.505-97.289-9.684-4.138 1.255-8.514-1.081-9.768-5.219-1.254-4.14 1.08-8.513 5.221-9.771 29.581-8.98 78.756-7.245 109.83 11.202 3.73 2.209 4.95 7.016 2.74 10.733-2.2 3.722-7.02 4.949-10.73 2.739z"/>
            </svg>
        </div>

        <div class="barsContainer">
            <Bar v-for="(bH, i) in barHeights" :key="i" :h="bH" />
        </div>
    </div>

    <button class="refreshButton" @click="randomBars()">♻️</button>
</template>

<script lang="ts">
import { defineAsyncComponent, defineComponent } from 'vue';

/**
 * interesting that spotify URIs are 22 digits + 1 identifier (playlist, track, artist, etc) and there are 23 bars in spotify code
 *
 * UID
 * 6qDOv7xQDEShEPEdFtS5hQ
 *
 *
 * NOTE!
 * first, last and middle bars never change!
 *
 */

/**
 * spotify code gens from online:
 * https://www.spotifycodes.com/#create
 * + watch network activity or see below http get + res
 *
 * https://scannables.scdn.co/uri/plain/svg/000000/white/640/spotify:playlist:4w449zjyDnhIMj1qR7RYpX
 * https://scannables.scdn.co/uri/plain/svg/000000/white/640/spotify:playlist:37i9dQZEVXcRtmN4CL2mPL
 * https://scannables.scdn.co/uri/plain/svg/000000/white/640/spotify:playlist:4w449zjyDnhIMj1qR7RYpX
 * https://scannables.scdn.co/uri/plain/svg/000000/white/640/spotify:playlist:6J3zhFv39wFztScriqL5tP
 * https://scannables.scdn.co/uri/plain/svg/000000/white/640/spotify:playlist:6qDOv7xQDEShEPEdFtS5hQ
 *
 * https://scannables.scdn.co/uri/plain/svg/000000/white/640/spotify:track:522A3dgrvWe27tK3L3gbYF
 * https://scannables.scdn.co/uri/plain/svg/000000/white/640/spotify:track:09Z3vqWLXnpCytqf3vZfEy
 */

// helper from processing
function map_range(value, low1, high1, low2, high2) {
    return low2 + (high2 - low2) * (value - low1) / (high1 - low1);
}

export default defineComponent({
    name: 'SpotCode',
    components: {
        Bar: defineAsyncComponent(() => import('./Bar.vue'))
    },
	data() {
		return {
            hello: 'world',
            colors: {
                foreground: '#fff',
                background: '#4d4d4d'
            },

            // 23 bars
            numBars: 23,
            barHeights: []

		}
    },
    mounted() {
        this.randomBars();
    },
    methods: {
        randomBars() {
            for (let i = 0; i < this.numBars; i++) {
                if (i == 0 || i == this.numBars - 1) {
                    this.barHeights[i] = 10;
                } else if (i == 11) {
                    this.barHeights[i] = 52;
                } else {
                    const random = Math.random();
                    this.barHeights[i] = map_range(random, 0, 1, 10, 52);
                }

            }
        }
    }
});
</script>

<style scoped>
.spotCodeContainer {
    background: #4d4d4d;
    width: 300px;
    height: 60px;
    border-radius: 6px;

    padding: 8px 12px;

    display: flex;
}

.spotifyLogo {
    /* width: 43px;
    max-width: 43px; */
    height: 100%;
    /* max-height: 60px; */
    flex-basis: 42px;

    padding: 0 3px 0 1px;
}

.barsContainer {
    width: 240px;
    height: 100%;
    /* background: pink; */

    display: flex;
    align-items: center;

    padding: 0 10px;
}

.refreshButton {
    font-size: 24px;
    margin: 36px 0;
}
</style>