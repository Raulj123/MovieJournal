<script>
	import MovieInput from './movie.svelte';
	import MovieList from './movieList.svelte';

	let movies = localStorage.getItem('movies') ?
	JSON.parse(localStorage.getItem('movies')) :
	[];

	const submitMovie = movie =>{
		console.log(movie);
		const updatedMovies = [...movies, movie]	//all movies w the new movie 
		localStorage.setItem('movies', JSON.stringify(updatedMovies));	//set updates movies to local
		movies = updatedMovies;		// 
	}
</script>

<main>
	<div class="main">
		<h1>Movie Journal</h1>
		<MovieInput on:submitMovie={event => submitMovie(event.detail.movie)}/>
		<MovieList movies={movies}/>
	</div>
</main>

<style>
	.main{

	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>