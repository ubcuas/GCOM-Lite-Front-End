<script>
	import Mapnav from './mapnav.svelte';
	import Aerialview from './aerialview.svelte';
	import Metrics from './metrics.svelte';
	import Waypoints from './waypoints.svelte';
</script>

<!---------------->
<body>
	<header>
		<Mapnav />
	</header>
	<div class="container m-0 p-0">
		<div class="row">
			<div class="col"><Metrics /></div>
			<div class="col"><Aerialview /></div>
		</div>
		<div class="row">
			<div class="col">
				<Waypoints />
			</div>
		</div>
	</div>
</body>

<!---------------->
<style>
	.container {
		min-width: 100%;
	}
</style>
