<script>
	import BookCard from './BookCard.svelte';
	export let name;
	let title = '';
	let price = 0;
	let description = '';

	let books = [];
	function handleAddBook() {
		books = books.concat({
			title,
			price,
			description
		});
		title = '';
		price = 0;
		description = '';
	}
</script>

<main>
	<h1>Welcome to {name}'s online bookstore!</h1>
	<section>
		<h2>Add new book</h2>
		<label for="title">Title</label>
		<input type="text" id="title" bind:value={title}>
		<label for="price">price</label>
		<input type="number" id="price" bind:value={price}>
		<label for="description">Description</label>
		<textarea name="description" id="description" rows="3" bind:value={description}></textarea>
		<div>
			<button on:click={handleAddBook}>add book</button>
		</div>
		{#each books as book} 
			<BookCard title={book.title} price={book.price} description={book.description} />
		{/each}
		
	</section>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
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