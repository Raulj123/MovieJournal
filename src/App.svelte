<script>
	import MovieInput from './movie.svelte';
	import MovieList from './movieList.svelte';
	import Search from './search.svelte'
	let movies = localStorage.getItem('movies') ?
	JSON.parse(localStorage.getItem('movies')) :
	[];

	const submitMovie = movie =>{
		console.log(movie);
		const updatedMovies = [...movies, movie]	//all movies w the new movie 
		localStorage.setItem('movies', JSON.stringify(updatedMovies));	//set updates movies to local
		movies = updatedMovies;		// 
	}

	const clearSearch = ()=>{
		let movies = localStorage.getItem('movies') ?
	JSON.parse(localStorage.getItem('movies')) :
	[];
	};

	const search = (searchTerm) =>{
		const tempMovies = localStorage.getItem('movies') ?
		JSON.parse(localStorage.getItem('movies')):[];

		movies = tempMovies.filter(m => 
		m.title.toLowerCase().includes(searchTerm.toLowerCase()));

	};
</script>

<main style="background-color:#f5f5dc;">
	<div class="main">
		<h1>Movie Journal</h1>
		<Search on:clearSearch={clearSearch} on:search ={e =>search(e.detail.searchTerm)}/>
		<MovieInput on:submitMovie={event => submitMovie(event.detail.movie)}/>
		<MovieList movies={movies}/>
	</div>
	<footer >Made with 💖 by Raul </footer>
   
</main>

<style>
	.main{
		background-color: #f5f5dc;
		width: 500px;
		max-width: 100%;
		padding:1em;
		margin: auto;
		text-align: center;
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