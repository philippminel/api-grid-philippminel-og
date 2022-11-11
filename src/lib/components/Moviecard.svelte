<script>
    export let movieInput;
</script>


<div class="movie">
	<img src={'https://image.tmdb.org/t/p/w500/' + movieInput.poster_path} alt={movieInput.title} />
	<h2>{movieInput.title}</h2>
</div>

<style>
    img {
        width: 100%;
        transition: all 0.5s;
        border-radius: 5%;
        box-shadow: 0px 0px 4px 6px black;

    }
    
    .movie:hover{
        transform: scale(1.1);
        transition:all 0.5s;
        opacity: 1.0;
    }

    .movie{
        opacity: 0.7;
        transition:all 0.5s;
    }
    img:hover {
        box-shadow: 0px 0px 4px 4px white;
    }

    h2{
        color: whitesmoke;
        font-size: 18px;
        transition: all 0.5s;
    }



</style>