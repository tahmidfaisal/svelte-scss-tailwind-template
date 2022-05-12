<script lang="ts">
	import Tailwindcss from './Tailwindcss.svelte';
	import "../node_modules/bulma/css/bulma.css";
	export let name: string;
</script>

<Tailwindcss />
<main>
	<button class="box hover:!bg-red-700 !bg-blue-100">Hello {name}!</button>
</main>

<style style="scss">
</style>
