<script>
import { SITE_NAME } from '$lib/config.js';
import ShapeOutsideFix from '$lib/ShapeOutsideFix.svelte';
import ZoomImg from '$lib/ZoomImg.svelte';
</script>

<ShapeOutsideFix />

<div class="pageContainer" style="display:block">
	<div class="pageLeft">
		<span class="goodText">about</span>
	</div>
	<div class="hrContainer">
		<hr>
	</div>
</div>

<div class="pageContainer">
	<div class="pageLeft">
		<!-- <ZoomImg src="/Images/284757.png" alt="example" style="float: left; width: 200px; margin: 0 1.5rem 1rem 0; shape-outside: url(/Images/284757.png);" /> -->
		<span class="goodText">the site</span>
		<p>{SITE_NAME} is a personal blog. Replace this with a description of what your blog is about and what readers can expect to find here.</p>
		<p>You can edit this page at <code>src/routes/about/+page.svelte</code>.</p>
	</div>
	<div class="pageRight">
		<!-- <ZoomImg src="/Images/pngegg.png" alt="example" style="float: right; width: 200px; margin: 0 0 1rem 1.5rem; shape-outside: url(/Images/pngegg.png);" /> -->
		<span class="goodText">me</span>
		<span class="tinyText" style="margin-left: 10px;">pro/nouns</span>
		<p>Write a bit about yourself here. Who are you, what do you do, what are you interested in.</p>
		<p>You can add contact info, links to social media, or anything else you want people to know.</p>
	</div>
</div>

<style>
code {
	background: #333;
	padding: 0.1em 0.4em;
	border-radius: 3px;
	font-size: 0.85em;
}

@media (max-width: 767px) {
	.goodText {
		font-size: 40px;
	}
}
</style>
