<script>
    import {page} from '$app/stores';
    import { onMount } from 'svelte';
    import Play from'$lib/images/Play.svelte';
	// import Moviecard from '../../../lib/components/Moviecard.svelte';
    
    

    console.log($page.params.id);

    let movieID = $page.params.id;
    let movie = null;

    onMount(async function () {
		const response = await fetch(
			'https://api.themoviedb.org/3/movie/'+ movieID +
            '?api_key=e277d7dac1b4511a5ee2e5993a83d923&language=en-US'
		);

		const answer = await response.json();
        movie = answer;
		console.log(movie);
	});
</script>

<a href="/">Home</a> 


{#if movie}  
<div id="movieContainer">
    <div class="movieCard">
        <img src={'https://image.tmdb.org/t/p/w500/' + movie.poster_path} alt={movie.title} />
        <div class="cardDetails">
            <div class="movieDetails">
                <div class="info"><p1>{movie.runtime} min</p1></div>
                <div class="info"><p1>{movie.release_date}</p1></div>
            </div>
                <div class="movieTitle"><h1>{movie.title}</h1></div>
                <div class="overview"><p>{movie.overview}</p></div>
                <Play />
            <div class="genres">
                {#each movie.genres as genre} 
		            <p>{genre.name}</p>
	            {/each}
            </div>
        </div>
    </div>
</div>
{:else}
    <h1>Loading...</h1>
{/if}


<style>
    a{
        color: white;
        text-decoration: none;
    }

    h1{
		font-size: 35pt; 
    }
    .movieCard{
        padding: 60px 50px;
        width: 1281px;
		height: 692px;
        left: 116px;
        top: 100px;
        position: absolute;
        background-color: rgb(57, 57, 57);
        border-radius: 44px;
        display: flex;
        gap: 50px;
    }

    .movieDetails{
        display: flex;
        flex-direction: row;
        color: grey;
        justify-content: flex-end;
        gap: 30px;
        /* top: 155px; */
        /* left: 1000px; */
    }


    img {
        border-radius: 5%;
        width: 375px;
        height: 572px;
        top: 100px;
        left: 500px;
        box-shadow: 2px 6px 15px 7px;
    }
        
    .cardDetails {
        display: flex;
        flex-direction: column;
        /* gap: 30px; */
        /* justify-content: space-between; */
        max-width: 680px;
    }

    .movieTitle{
        font-size: 35pt;
        color: white;
        margin-top: 100px;
    }

    
    .overview{
        color:white;
        padding-top: 30px;
        padding-bottom: 50px;
    }

    .genres{
        display: flex;
        flex-direction: row;
        color: grey;
        justify-content: flex-end;
        gap: 30px;
    }

</style>

