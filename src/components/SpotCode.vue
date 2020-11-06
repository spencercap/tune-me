<template>
	<!-- <div class="spotCodeContainer">
		<div class="spotifyLogo">
			<svg
				xmlns="http://www.w3.org/2000/svg"
				height="100%"
				width="100%"
				version="1.1"
				viewBox="0 0 168 168"
			>
				<path
					:fill="colors.foreground"
					d="m83.996 0.277c-46.249 0-83.743 37.493-83.743 83.742 0 46.251 37.494 83.741 83.743 83.741 46.254 0 83.744-37.49 83.744-83.741 0-46.246-37.49-83.738-83.745-83.738l0.001-0.004zm38.404 120.78c-1.5 2.46-4.72 3.24-7.18 1.73-19.662-12.01-44.414-14.73-73.564-8.07-2.809 0.64-5.609-1.12-6.249-3.93-0.643-2.81 1.11-5.61 3.926-6.25 31.9-7.291 59.263-4.15 81.337 9.34 2.46 1.51 3.24 4.72 1.73 7.18zm10.25-22.805c-1.89 3.075-5.91 4.045-8.98 2.155-22.51-13.839-56.823-17.846-83.448-9.764-3.453 1.043-7.1-0.903-8.148-4.35-1.04-3.453 0.907-7.093 4.354-8.143 30.413-9.228 68.222-4.758 94.072 11.127 3.07 1.89 4.04 5.91 2.15 8.976v-0.001zm0.88-23.744c-26.99-16.031-71.52-17.505-97.289-9.684-4.138 1.255-8.514-1.081-9.768-5.219-1.254-4.14 1.08-8.513 5.221-9.771 29.581-8.98 78.756-7.245 109.83 11.202 3.73 2.209 4.95 7.016 2.74 10.733-2.2 3.722-7.02 4.949-10.73 2.739z"
				/>
			</svg>
		</div>

		<div class="barsContainer">
			<Bar v-for="(bH, i) in barHeights" :key="i" :h="bH" />
		</div>
	</div> -->

	<!-- <img :src="currentTrackCodeUrl" alt="" /> -->

	<svg
		class="spotCodeSvg"
		width="256"
		height="64"
		viewBox="0 0 400 100"
		xmlns="http://www.w3.org/2000/svg"
		xmlns:xlink="http://www.w3.org/1999/xlink"
	>
		<rect
			x="0"
			y="0"
			width="400"
			height="100"
			:fill="`hsl(${codeBg.h}deg 100% 50%)`"
			:style="`fill: hsl(${codeBg.h}deg 100% 50%) !important`"
		/>
		<!-- :fill="`hsl(${codeBg.r} ${codeBg.g} ${codeBg.b})`"
		:style="`fill: rgb(${codeBg.r} ${codeBg.g} ${codeBg.b}) !important`" -->
		<rect
			v-for="(bar, i) in currentTrackBars"
			:key="i"
			:x="bar.x"
			:y="bar.y"
			:width="bar.w"
			:height="bar.h"
			rx="3.36"
			ry="3.36"
			:fill="colors.foreground"
		/>
		<g transform="translate(20,20)">
			<path
				:fill="colors.foreground"
				d="M30,0A30,30,0,1,1,0,30,30,30,0,0,1,30,0M43.73,43.2a1.85,1.85,0,0,0-.47-2.43,5,5,0,0,0-.48-.31,30.64,30.64,0,0,0-5.92-2.72,37.07,37.07,0,0,0-11.56-1.84c-1.33.07-2.67.12-4,.23a52.44,52.44,0,0,0-7.08,1.12,3.45,3.45,0,0,0-.54.16,1.83,1.83,0,0,0-1.11,2.08A1.79,1.79,0,0,0,14.37,41a4.29,4.29,0,0,0,.88-.12,48.93,48.93,0,0,1,8.66-1.15,35.33,35.33,0,0,1,6.75.37,28.29,28.29,0,0,1,10.25,3.61,4.77,4.77,0,0,0,.5.27,1.85,1.85,0,0,0,2.33-.74M47.41,35a2.34,2.34,0,0,0-.78-3.19l-.35-.21a35.72,35.72,0,0,0-7.38-3.3,45.39,45.39,0,0,0-15.7-2.13,41.19,41.19,0,0,0-7.39.92c-1,.22-2,.48-2.94.77A2.26,2.26,0,0,0,11.29,30a2.32,2.32,0,0,0,1.44,2.2,2.47,2.47,0,0,0,1.67,0,37,37,0,0,1,10.38-1.46,43,43,0,0,1,7.91.74,35.46,35.46,0,0,1,9.58,3.18c.66.34,1.3.72,1.95,1.08A2.33,2.33,0,0,0,47.41,35m.35-8.49A2.79,2.79,0,0,0,52,24.11c0-.2,0-.4-.08-.6a2.78,2.78,0,0,0-1.4-1.85,35.91,35.91,0,0,0-6.41-2.91,56.19,56.19,0,0,0-16.86-2.89,58.46,58.46,0,0,0-7,.21,48.31,48.31,0,0,0-6.52,1c-.87.2-1.73.42-2.58.7a2.73,2.73,0,0,0-1.85,2.68,2.79,2.79,0,0,0,2,2.61,2.9,2.9,0,0,0,1.6,0c.87-.23,1.75-.47,2.63-.66a45.52,45.52,0,0,1,7.26-.91,57.42,57.42,0,0,1,6.4,0,53.7,53.7,0,0,1,6.11.72,42.63,42.63,0,0,1,8.49,2.35,33.25,33.25,0,0,1,4,2"
			/>
		</g>
	</svg>

	<button class="refreshButton" @click="getRandomSong()">🎈</button>
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
 * native api for GET Spotify code:
 * fetch('https://scannables.scdn.co/uri/plain/svg/000000/white/640/spotify:playlist:4w449zjyDnhIMj1qR7RYpX').then(response => console.log(response));
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
	return low2 + ((high2 - low2) * (value - low1)) / (high1 - low1);
}

// helper from @perryjanssen - https://medium.com/@perryjanssen/getting-random-tracks-using-the-spotify-api-61889b0c0c27
function getRandomSearch(): string {
	// A list of all characters that can be chosen.
	const characters = 'abcdefghijklmnopqrstuvwxyz 1234567890';

	// Gets a random character from the characters string.
	const randomCharacter = characters.charAt(
		Math.floor(Math.random() * characters.length)
	);
	let randomSearch = '';

	// Places the wildcard character at the beginning, or both beginning and end, randomly.
	switch (Math.round(Math.random())) {
		case 0:
			randomSearch = randomCharacter + '*';
			break;
		case 1:
			randomSearch = '*' + randomCharacter + '*';
			break;
	}

	return randomSearch;
}

export default defineComponent({
	name: 'SpotCode',
	components: {
		Bar: defineAsyncComponent(() => import('./Bar.vue')),
	},
	data() {
		return {
			hello: 'world',
			colors: {
				foreground: '#fff',
				background: '#4d4d4d',
			},

			// 23 bars
			numBars: 23,
			barHeights: [] as number[],

			spotifyAccessToken: '',

			currentTrackId: '',
			currentTrackCodeUrl: '',
			currentTrackBars: [
				{ x: 100, y: 44.5, w: 6.710000038146973, h: 11 },
				{ x: 112.41999816894531, y: 37.5, w: 6.710000038146973, h: 25 },
				{ x: 124.83999633789062, y: 20, w: 6.710000038146973, h: 60 },
				{ x: 137.27000427246094, y: 37.5, w: 6.710000038146973, h: 25 },
				{ x: 149.69000244140625, y: 37.5, w: 6.710000038146973, h: 25 },
				{ x: 162.11000061035156, y: 41, w: 6.710000038146973, h: 18 },
				{ x: 174.52999877929688, y: 27, w: 6.710000038146973, h: 46 },
				{ x: 186.9600067138672, y: 30.5, w: 6.710000038146973, h: 39 },
				{ x: 199.3800048828125, y: 27, w: 6.710000038146973, h: 46 },
				{ x: 211.8000030517578, y: 34, w: 6.710000038146973, h: 32 },
				{ x: 224.22000122070312, y: 44.5, w: 6.710000038146973, h: 11 },
				{ x: 236.63999938964844, y: 20, w: 6.710000038146973, h: 60 },
				{ x: 249.07000732421875, y: 37.5, w: 6.710000038146973, h: 25 },
				{ x: 261.489990234375, y: 41, w: 6.710000038146973, h: 18 },
				{ x: 273.9100036621094, y: 20, w: 6.710000038146973, h: 60 },
				{ x: 286.3299865722656, y: 37.5, w: 6.710000038146973, h: 25 },
				{ x: 298.760009765625, y: 41, w: 6.710000038146973, h: 18 },
				{ x: 311.17999267578125, y: 41, w: 6.710000038146973, h: 18 },
				{ x: 323.6000061035156, y: 30.5, w: 6.710000038146973, h: 39 },
				{ x: 336.0199890136719, y: 20, w: 6.710000038146973, h: 60 },
				{ x: 348.44000244140625, y: 27, w: 6.710000038146973, h: 46 },
				{ x: 360.8699951171875, y: 41, w: 6.710000038146973, h: 18 },
				{ x: 373.2900085449219, y: 44.5, w: 6.710000038146973, h: 11 },
			] as { x: number; y: number; w: number; h: number }[],

			codeBg: {
				h: 53, // hue
				r: '255',
				g: '255',
				b: '255',
			},
		};
	},
	mounted() {
		this.authSpotify();

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
		},

		async authSpotify() {
			// auth via Client Credentials Flow:
			// https://developer.spotify.com/documentation/general/guides/authorization-guide/#client-credentials-flow
			console.log('authSpotify started');

			const SPOTIFY_CLIENT_ID = '5a0615f4cf8948baa92feb3a46787f92';
			const SPOTIFY_CLIENT_SECRET = '53daf5908be14c7a953f60ea15a4a760';
			const SpotAuthBase64 = btoa(
				`${SPOTIFY_CLIENT_ID}:${SPOTIFY_CLIENT_SECRET}`
			);

			const res = await fetch('https://accounts.spotify.com/api/token', {
				method: 'POST',
				headers: {
					'Content-Type': 'application/x-www-form-urlencoded',
					Authorization: `Basic ${SpotAuthBase64}`,
				},
				body: new URLSearchParams({
					grant_type: 'client_credentials',
				}),
			});

			if (res && res.ok) {
				const data = await res.json();
				// console.log(data);

				if (data && data.access_token) {
					this.spotifyAccessToken = data.access_token as string;

					// get a random song on first init
					this.getRandomSong();
				} else {
					alert('sorry - this dont twerk no moe (2)');
				}
			} else {
				alert('sorry - this dont twerk no moe (1)');
			}
		},

		setRandomCodeBg() {
			const COLOR_MIN = 130;
			const COLOR_MAX = 255;
			const r = map_range(Math.random(), 0, 1, COLOR_MIN, COLOR_MAX);
			const g = map_range(Math.random(), 0, 1, COLOR_MIN, COLOR_MAX);
			const b = map_range(Math.random(), 0, 1, COLOR_MIN, COLOR_MAX);

			const h = Math.floor(Math.random() * 259);

			this.codeBg = {
				r,
				b,
				g,

				h,
			};
		},

		async getRandomSong() {
			// console.log('getRandomSong started');

			this.setRandomCodeBg();

			const SPOTIFY_MAX_OFFSET = 2000;
			const type = 'track';
			const q = getRandomSearch();
			const offset = Math.floor(Math.random() * SPOTIFY_MAX_OFFSET);
			const limit = 1; // just get 1 song (:
			const req = `https://api.spotify.com/v1/search?type=${type}&q=${q}&offset=${offset}&limit=${limit}`;

			const res = await fetch(req, {
				method: 'GET',
				headers: {
					Authorization: `Bearer ${this.spotifyAccessToken}`,
				},
			});

			if (res && res.ok) {
				const data = await res.json();
				// console.log(data);

				if (data) {
					const track = data.tracks.items[0];
					// console.log('track.id', track.id);
					this.currentTrackId = track.id;
					this.getSpotifyCodeFromTrackId(track.id);
					this.currentTrackCodeUrl = `https://scannables.scdn.co/uri/plain/svg/000000/white/256/spotify:track:${track.id}`;
				} else {
					alert('sorry - couldnt get a song (4)');
				}
			} else {
				// alert('sorry - couldnt get a song (3)');
				console.error('sorry - couldnt get a song (3)');
			}
		},

		async getSpotifyCodeFromTrackId(inTrackId: string) {
			console.log('getSpotifyCodeFromTrackId started', inTrackId);

			const res = await fetch(
				`https://scannables.scdn.co/uri/plain/svg/000000/white/256/spotify:track:${inTrackId}`
			);
			// console.log(res);

			if (res && res.ok) {
				if (res.url) {
					// console.log('res.url', res.url);
					// this.currentTrackCodeUrl = res.url;
				} else {
					alert('sorry - couldnt get a spotify code (6)');
				}

				const blob = await res.blob();
				const svgText = await blob.text();
				// console.log('svgText', svgText);
				const svgParser = new DOMParser();
				const svg = svgParser.parseFromString(svgText, 'image/svg+xml');
				// console.log(svg);
				const rectNodeList = svg.querySelectorAll('rect');
				const bars = Array.prototype.slice.call(rectNodeList);
				bars.shift(); // remove first rect (background)

				bars.forEach((bar, i) => {
					this.currentTrackBars[i] = {
						x: bar.x.baseVal.value,
						y: bar.y.baseVal.value,
						w: bar.width.baseVal.value,
						h: bar.height.baseVal.value,
					};
				});
			} else {
				alert('sorry - couldnt get a spotify code (5)');
			}
		},
	},
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

	display: flex;
	align-items: center;

	padding: 0 10px;
}

.refreshButton {
	width: 45px;
	height: 45px;
	font-size: 32px;
	background: #fff;
	border-radius: 4px;
	border: 2px solid #000;
	margin: 24px 0;
	/* margin-bottom: 16px; */
	cursor: pointer;
}
.refreshButton:hover {
	box-shadow: 2px 2px 0 #000;
}
.refreshButton:active,
.refreshButton:focus {
	outline: none;
}

.spotCodeSvg {
	border-radius: 6px;
	margin-top: 64px;
}

rect {
	transition: height 0.3s ease-out, y 0.3s ease-out, fill 1s;
}

svg * {
	fill: white;
	mix-blend-mode: difference;
}
</style>
