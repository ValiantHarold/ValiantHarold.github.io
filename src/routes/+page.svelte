<script lang="ts">
	let count = 0;
</script>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-5">
		<h1 class="h1">ValiantWolf's Portfolio</h1>
		<h2>Counter: {count}</h2>
		<button on:click={() => count++}>Increase</button>
		<button on:click={() => count--}>Decrease</button>
	</div>
</div>
