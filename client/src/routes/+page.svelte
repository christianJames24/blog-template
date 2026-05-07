<script>
import posts from '$lib/posts.json';
import { SITE_NAME, SITE_TAGLINE } from '$lib/config.js';
import ZoomImg from '$lib/ZoomImg.svelte';

const sorted = [...posts].sort((a, b) => new Date(b.date) - new Date(a.date));
const latest = sorted[0];
const recent = sorted.slice(0, 3);
</script>

<div class="home">
	<div class="hero">
		<div class="hero-text">
			<span class="goodText title">{SITE_NAME}</span>
			<p class="tagline">{SITE_TAGLINE}</p>
		</div>
		<ZoomImg src="/Images/r2_988d0b7f-fe97-47fd-aafe-fc292b955fac.png" alt="mascot" style="width: 300px; object-fit: contain;" />
	</div>

	<div class="nav-row">
		<a class="nav-pill whiteHover" href="/posts">posts</a>
		<a class="nav-pill whiteHover" href="/about">about</a>
	</div>

	{#if latest}
		<div class="section">
			<p class="label">latest post</p>
			<a class="featured" href="/posts/{latest.slug}">
				<span class="featured-title">{latest.title}</span>
				<span class="featured-meta">
					<span class="featured-date">{latest.date}</span>
					<span class="featured-arrow">></span>
				</span>
			</a>
		</div>
	{/if}

	{#if recent.length > 1}
		<div class="section">
			<p class="label">recent</p>
			<div class="recent-list">
				{#each recent.slice(1) as post}
					<a class="recent-item" href="/posts/{post.slug}">
						<span>{post.title}</span>
						<span class="recent-date">{post.date}</span>
					</a>
				{/each}
			</div>
		</div>
	{/if}
</div>

<style>
.home {
	padding: 25px;
	max-width: 700px;
}

.hero {
	display: flex;
	align-items: center;
	gap: 1.5rem;
	margin-bottom: 1.5rem;
}

.hero-text {
	flex: 1;
}

.title {
	display: block;
}

.tagline {
	color: #888;
	font-size: 1rem;
	margin-top: 0.25rem;
}

.nav-row {
	display: flex;
	gap: 0.5rem;
	margin-bottom: 2rem;
}

.nav-pill {
	padding: 0.4rem 1rem;
	background: #222;
	border: 1px solid #333;
	font-size: 0.85rem;
	text-decoration: none;
}

.nav-pill:hover {
	border-color: #555;
}

.section {
	margin-bottom: 1.5rem;
}

.label {
	color: #888;
	font-size: 0.75rem;
	text-transform: uppercase;
	letter-spacing: 0.15em;
	margin-bottom: 0.5rem;
}

.featured {
	display: flex;
	justify-content: space-between;
	align-items: center;
	background: #222;
	border: 1px solid #333;
	padding: 1.2rem 1.4rem;
	text-decoration: none;
	color: #fff;
	font-size: 1.15rem;
}

.featured:hover {
	border-color: #555;
}

.featured-title {
	flex: 1;
}

.featured-meta {
	display: flex;
	align-items: center;
	gap: 0.75rem;
}

.featured-date {
	color: #666;
	font-size: 0.8rem;
}

.featured-arrow {
	color: #888;
	font-size: 1.2rem;
}

.recent-list {
	display: flex;
	flex-direction: column;
	gap: 1px;
}

.recent-item {
	display: flex;
	justify-content: space-between;
	align-items: center;
	padding: 0.7rem 1rem;
	background: #222;
	border: 1px solid #333;
	text-decoration: none;
	color: #c4c4c4;
	font-size: 0.95rem;
}

.recent-item:hover {
	border-color: #ffb347;
	color: #fff;
}

.recent-date {
	color: #555;
	font-size: 0.8rem;
}

@media (max-width: 767px) {
	.home {
		padding: 12px;
	}

	.title {
		font-size: 40px;
	}

	.featured {
		flex-direction: column;
		align-items: flex-start;
		gap: 0.5rem;
		padding: 1rem;
		font-size: 1rem;
	}

	.recent-item {
		font-size: 0.85rem;
		padding: 0.6rem 0.8rem;
	}
}

@media (max-width: 400px) {
	.title {
		font-size: 32px;
	}
}
</style>
