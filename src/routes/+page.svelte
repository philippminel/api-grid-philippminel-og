<script>
	import { onMount } from 'svelte';
	import Moviecard from '$lib/components/Moviecard.svelte'


	let movies = [];

	//diese Funktion wird ausgeführt sobald die Komponente (in diesem Fall die Seite) geladen wird.
	onMount(async function () {
		const response = await fetch(
			'https://api.themoviedb.org/3/trending/movie/day?api_key=e277d7dac1b4511a5ee2e5993a83d923'
		);

		const answer = await response.json();
		movies = answer.results;
		console.log(movies[1]);
	});
</script>

<!-- Hier sollen die Filme im Grid dargestellt werden: -->
<h1>Trending Movies</h1>

<div class = "container">
	{#each movies as movie} 
		<Moviecard movieInput={movie}></Moviecard>
	{/each}
</div>

<style>

.container{
	display: grid;
	grid-template-columns: repeat(auto-fill, minmax(150px,1fr));
	/* grid-template-columns:  */
	gap: 25px;
	margin-top: 130px;

}
	h1{
		color: whitesmoke;
		margin-top: 50px;
		font-size: 40pt;
	}
</style>
