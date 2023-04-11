<script>
    export let movies;


</script>

{#each movies as movie(movie.title)} 
    <div>
        <h3>{movie.title}</h3>
        <p>Rating: {movie.rating}</p>
    </div>


{/each}