<script>
import { onMount } from 'svelte';

onMount(() => {
	document.querySelectorAll('img[style*="shape-outside"]').forEach(img => {
		const forceReflow = () => {
			img.style.display = 'none';
			img.offsetHeight;
			img.style.display = '';
		};
		if (img.complete) forceReflow();
		else img.addEventListener('load', forceReflow);
	});
});
</script>
