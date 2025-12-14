<script lang="ts">
	import Header from '@core/Header.svelte';
	import '../styles/layout.css';

	let { children } = $props();
</script>

<div class="app min-h-screen flex flex-col">
	<!-- Global SVG Symbols -->
	<svg class="sr-only">
		<defs>
			<symbol id="icon-chevron-down" viewBox="0 0 24 24">
				<path d="M6 9l6 6 6-6" />
			</symbol>
			<symbol id="icon-chevron-right" viewBox="0 0 24 24">
				<path d="M9 6l6 6-6 6" />
			</symbol>
			<symbol id="icon-menu" viewBox="0 0 24 24">
				<path d="M3 12h18M3 6h18M3 18h18" />
			</symbol>
		</defs>
	</svg>

	<Header />

	<main class="flex-1 flex flex-col p-4 w-full max-w-4xl mx-auto box-border">
		{@render children()}
	</main>

	<footer class="flex flex-col justify-center items-center p-3 md:p-0">
		<p>
			visit <a href="https://svelte.dev/docs/kit" class="font-bold">svelte.dev/docs/kit</a> to learn about
			SvelteKit
		</p>
	</footer>
</div>
