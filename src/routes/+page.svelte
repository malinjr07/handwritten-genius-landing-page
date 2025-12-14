<script lang="ts">
	import Header from '@core/Header.svelte';
	import Button from '@common/Button.svelte';
</script>

<Header title="Handwritten Genius" />

<main class="p-4">
	<h2>Welcome to the app</h2>
	<p>This is the root page testing the new import aliases.</p>
	<Button onClick={() => alert('Button clicked!')}>
		{#snippet children()}Click Me!{/snippet}
	</Button>
</main>
