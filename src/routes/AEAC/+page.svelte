<script>
	import { Html5Qrcode } from 'html5-qrcode';
	import { onMount } from 'svelte';

	let scanning = false;

	/**
	 * @type {Html5Qrcode}
	 */
	let html5Qrcode;

	onMount(init);

	function init() {
		html5Qrcode = new Html5Qrcode('reader');
	}

	function start() {
		html5Qrcode.start(
			{ facingMode: 'environment' },
			{
				fps: 10,
				qrbox: { width: 250, height: 250 }
			},
			onScanSuccess,
			onScanFailure
		);
		scanning = true;
	}

	async function stop() {
		await html5Qrcode.stop();
		scanning = false;
	}

	/**
	 * @param {any} decodedText
	 * @param {any} decodedResult
	 */
	function onScanSuccess(decodedText, decodedResult) {
		alert(`Code matched = ${decodedText}`);
		console.log(decodedResult);

		async function doPost() {
			const res = await fetch('http://localhost:8080/', {
				method: 'POST',
				headers: {
					'Content-Type': 'application/json'
				},
				body: JSON.stringify({
					decodedText,
					decodedResult
				})
			});
			res.text().then((text) => {
				console.log(text);
			});

			// const json = await res.json()
			// result = JSON.stringify(json)
		}
		doPost();
		stop();
	}

	/**
	 * @param {any} error
	 */
	function onScanFailure(error) {
		console.warn(`Code scan error = ${error}`);
	}
</script>

<body>
	<h3>This is the AEAC Page. This page is currently under construction.</h3>
	<reader id="reader" />
	{#if scanning}
		<button class="btn" on:click={stop} id="stop">Stop Scanning</button>
	{:else}
		<button class="btn" on:click={start} id="start"> Initialize Scan</button>
	{/if}
</body>

<style>
	body {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		gap: 20px;
	}
	reader {
		width: 350px;
		min-height: 250px;
		background-color: black;
	}
	.btn {
		border: none;
		width: 500px;
		height: 90px;
		border-radius: 50px;
		cursor: pointer;
		font-size: 20px;
		text-transform: uppercase;
		letter-spacing: 10px;
		font-weight: bold;
		box-shadow: 0 8px 10px rgba(0, 0, 0, 0.1);
		transition: box-shadow 0.3s ease, background-color 0.3s ease, color 0.3s ease;
		margin-bottom: 2rem;
	}
	.btn:hover {
		background-color: #2da0dc;
		transform: translateY(-7px);
		color: #fff;
		box-shadow: 0px 10px 15px rgba(46, 223, 229, 0.4);
		margin-bottom: 2rem;
	}
</style>
