<script lang="ts">
	import Tailwindcss from "./Tailwindcss.svelte";
	import "../node_modules/bulma/css/bulma.css";
	import { onMount } from "svelte";
	export let name: string;

	let theme: string;
	onMount(() => {
		if (
			localStorage.theme === "dark" ||
			(!("theme" in localStorage) &&
				window.matchMedia("(prefers-color-scheme: dark)").matches)
		) {
			document.documentElement.classList.add("dark");
		} else {
			document.documentElement.classList.remove("dark");
		}
	});
	$: {
		(theme);
		if (
			localStorage.theme === "dark" ||
			(!("theme" in localStorage) &&
				window.matchMedia("(prefers-color-scheme: dark)").matches)
		) {
			document.documentElement.classList.add("dark");
		} else {
			document.documentElement.classList.remove("dark");
		}
	}

	// Whenever the user explicitly chooses light mode
	const lightTheme = () => {
		localStorage.theme = "light";
		theme = "light";
	};

	// Whenever the user explicitly chooses dark mode

	const darkTheme = () => {
		localStorage.theme = "dark";
		theme = "dark";
	};

	// Whenever the user explicitly chooses to respect the OS preference
	const systemTheme = () => {
		if (
			localStorage.theme === "dark" ||
			(!("theme" in localStorage) &&
				window.matchMedia("(prefers-color-scheme: dark)").matches)
		) {8
		document.documentElement.classList.add("dark");
			theme = "dark";
		} else {
			document.documentElement.classList.remove("dark");
			theme = "light";
		}
	};

	const toggleTheme = () => {
		if (localStorage.theme === "light") {
			darkTheme();
		} else if (localStorage.theme === "dark") {
			lightTheme();
		} else {
			throw Error("Unknown theme");
		}
	};
</script>

<Tailwindcss />
<main>
	{localStorage.theme}
	<button
		on:click={toggleTheme}
		class="box hover:!bg-red-700 !bg-blue-100 dark:!bg-gray-400"
		>Hello {name}!</button
	>
</main>

<style style="scss">
</style>
