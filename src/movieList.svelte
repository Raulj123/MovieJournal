<script>
    export let movies;


</script>

{#each movies as movie(movie.title)} 
    <div>
        <h3>{movie.title}</h3>
        <p>Rating: {movie.rating}</p>
       <p>Description: {movie.description}</p>
    </div>


{/each}

<style>
    h3{
        color: #ff3e00;
    }
    div{
        overflow-y: auto;
        text-align: left;
        padding-bottom: 10px;
        border-bottom: 1px solid black;
    }
</style>