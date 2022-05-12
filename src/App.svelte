<script lang="ts">import Tailwindcss from "./Tailwindcss.svelte";
	import "../node_modules/bulma/css/bulma.css";
	export let name: string;
	
	if (
		localStorage.theme === "dark" ||
		(!("theme" in localStorage) &&
			window.matchMedia("(prefers-color-scheme: dark)").matches)
	) {
		document.documentElement.classList.add("dark");
	} else {
		document.documentElement.classList.remove("dark");
	}

	// Whenever the user explicitly chooses light mode
	const lightTheme = () => localStorage.theme = "light";

	// Whenever the user explicitly chooses dark mode
	const darkTheme = () => localStorage.theme = "dark";

	// Whenever the user explicitly chooses to respect the OS preference
	const systemTheme = () => localStorage.removeItem("theme");
	
</script>

<Tailwindcss />
<main>
	<button class="box hover:!bg-red-700 !bg-blue-100">Hello {name}!</button>
</main>

<style style="scss">
</style>
