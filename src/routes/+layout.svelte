
<script>
	import Header from './Header.svelte';
	import './styles.css';
</script>



<div class="app">
	<Header />
	
	<main>
		<slot />
	</main>
	
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		max-height: 100vh;
		overflow: hidden;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		min-width: 100vw;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}

</style>
