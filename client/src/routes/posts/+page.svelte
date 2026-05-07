<script>
import posts from '$lib/posts.json';

let search = $state('');
let sortOrder = $state('newest');

let filtered = $derived(
	[...posts]
		.filter(p => p.title.toLowerCase().includes(search.toLowerCase()))
		.sort((a, b) => {
			const diff = new Date(b.date) - new Date(a.date);
			return sortOrder === 'newest' ? diff : -diff;
		})
);
</script>

<div id="mainContainer">
	<span class="goodText">all posts</span>

	<div class="controls">
		<input class="search-input" type="text" placeholder="search..." bind:value={search} />
		<select class="sort-select" bind:value={sortOrder}>
			<option value="newest">newest first</option>
			<option value="oldest">oldest first</option>
		</select>
	</div>

	<table>
		<thead>
			<tr>
				<th>title</th>
				<th>date</th>
			</tr>
		</thead>
		<tbody>
			{#each filtered as post}
				<tr>
					<td><a class="whiteHover" href="/posts/{post.slug}">{post.title}</a></td>
					<td>{post.date}</td>
				</tr>
			{:else}
				<tr><td colspan="2" class="no-results">no posts found</td></tr>
			{/each}
		</tbody>
	</table>
</div>

<style>
.controls {
	display: flex;
	gap: 0.75rem;
	margin: 1rem 0;
	max-width: 600px;
}

.search-input {
	flex: 1;
	padding: 0.5rem 0.8rem;
	background: #222;
	border: 1px solid #333;
	color: #c4c4c4;
	font-family: inherit;
	font-size: 0.9rem;
	border-radius: 4px;
}

.search-input::placeholder {
	color: #666;
}

.search-input:focus {
	outline: none;
	border-color: #555;
}

.sort-select {
	padding: 0.5rem 0.8rem;
	background: #222;
	border: 1px solid #333;
	color: #c4c4c4;
	font-family: inherit;
	font-size: 0.9rem;
	border-radius: 4px;
	cursor: pointer;
}

.sort-select:focus {
	outline: none;
	border-color: #555;
}

table {
	background: #222;
	border-collapse: collapse;
	width: 100%;
	max-width: 600px;
}

th, td {
	padding: 0.75rem 1.2rem;
	text-align: left;
	border-bottom: 1px solid #333;
}

th {
	color: #888;
	font-size: 0.8rem;
	text-transform: uppercase;
	letter-spacing: 0.1em;
}

tbody tr:hover {
	background: #2c2c2c;
}

.no-results {
	color: #666;
	font-style: italic;
}

@media (max-width: 767px) {
	#mainContainer {
		padding: 0 4px;
	}
	:global(.goodText) {
		font-size: 40px;
	}
	.controls {
		flex-direction: column;
	}
	table {
		font-size: 0.85rem;
	}
	th, td {
		padding: 0.5rem 0.6rem;
	}
}
</style>
