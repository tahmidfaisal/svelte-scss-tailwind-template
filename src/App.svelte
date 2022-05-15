<script lang="ts">
	import Tailwindcss from "./Tailwindcss.svelte";
	import "../node_modules/bulma/css/bulma.css";
	export let name: string;

	// create a local storage theme variable and create functions to change theme to light, dark or default
	let theme: "dark"|"light" = localStorage.getItem("theme");

	$: {
		if (theme=="dark") {
			document.documentElement.classList.add('dark');
		}
		else {
			document.documentElement.classList.remove('dark');
		}
	}

	if (theme == null) {
		let newTheme;
		if (window.matchMedia && window.matchMedia("(prefers-color-scheme: dark)").matches) {
				newTheme = "dark";
		}
		else {
				newTheme = "light";
		}
		localStorage.setItem("theme", newTheme);
	}
	function changeTheme(newTheme: "dark"|"light"|"default") {
		if (newTheme=="default") {
			//get system theme
			if (window.matchMedia && window.matchMedia("(prefers-color-scheme: dark)").matches) {
				newTheme = "dark";
			}
			else {
				newTheme = "light";
			}
			return
		}
		else if (newTheme=="dark" | newTheme=="light" ) localStorage.setItem("theme", newTheme);
		else throw new Error("Invalid theme");
		theme = newTheme;
	}


</script>

<Tailwindcss />
<main
	<button class="box hover:!bg-red-700 !bg-yellow-100 dark:!bg-gray-400">Hello {name}!</button>
</main>

<style style="scss">
</style>
