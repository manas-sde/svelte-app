<!-- <script>
	export let name;
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
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
</style> -->
<!-- 
<script>
    import Book from './book.svelte'
    let title = '';
    let price = 0;
    let description = '';
    function setTitle(event){
        title = event.target.value;
    }
</script>
<style>
    h1 {
        color: purple;

    }
    section{
        margin: auto;
        width :30rem;

    }
    label,input,textarea{width: 100%}
</style>
<section>
    <div> 
        <label for="title">Title</label>
        <input type="text" id="title" value={title} on:input={setTitle}/>
    </div>
    <div>
        <label for="price">Price</label>
        <input type="number" id="price" value={price} bind:value={price}/>
    </div>
    <div>
        <label for="description">Description</label>
        <textarea rows="3" id="description" bind:value ={description}/>
    </div>
</section>
<Book bookTitle={title} bookPrice={price} bookDescription={description}/> -->





<script>
	import Book from './book.svelte'
	import Button from './button.svelte'
	import Purchase from './purchase.svelte'

	let title = '';
	let price = 0;
	let description = '';

	let books =[];
	let purchases = [];

	function setTitle(event){
		title = event.target.value;
	}

	function addBook(){
		const newBook = {
			title : title,
			price : price,
			description: description

		};
		books = books.concat(newBook)
	}

	function purchaseBook(event){
		const selectedTitle= event.detail;
		purchases = purchases.concat({
			...books.find(book => book.title === selectedTitle)
		});
	}

</script>

<style>
	h1 {
		color: purple;
		text-align:center;

	}

	section{
		margin: 1rem auto;
		width: 30rem;
	}

	label,input,textarea{width: 100%}
</style>

<h1>Book Store</h1>

<section>
	<h2>Add New Book</h2>
	<div>
		<label for="title">Title</label>
		<input type="text" id="title" value={title} on:input={setTitle}/>
	</div>

	<div>
		<label for="price"> Price</label>
		<input type="number" id="price" bind:value={price}/>
		<!-- <input type="number" id="price" value={price}/> -->
	</div>

	<div>
		<label for="description">Description</label>
		<textarea rows="3" id="description" bind:value={description}/>
	</div>

	<Button on:click={addBook}>ADD Book</Button>

</section>

<section>
	<h2>Stock</h2>
	{#if books.length === 0}
		<p>
			No books in stock.
		</p>
	{:else}
	{#each books as book}
		<Book bookTitle={book.title}
		bookPrice={book.price}
		bookDescription={book.description}
		on:buy={purchaseBook}
		/>
	{/each}
{/if}
</section>

<section>
	<Purchase books ={purchases}  />
</section>
