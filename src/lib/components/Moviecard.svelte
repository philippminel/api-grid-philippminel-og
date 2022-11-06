<script>
    export let movieInput;
</script>


<div>
	<img src={'https://image.tmdb.org/t/p/w500/' + movieInput.poster_path} alt={movieInput.title} />
	<h2>{movieInput.title}</h2>
</div>

<style>
    img {
	width: 100%;
    transition: all 0.5s;
    }
    
    img:hover {
      transform: scale(1.1);
    }

    h2{
        color: whitesmoke;
        font-size: 18px;
        transition: all 0.5s;
    }
    

</style>