<script>
	import Tailwindcss from './Tailwindcss.svelte';

	export let name;
</script>

<Tailwindcss />
<main>
	<button class="hover:!bg-red-700 !bg-blue-100">Hello {name}!</button>
</main>

<style>
</style>
