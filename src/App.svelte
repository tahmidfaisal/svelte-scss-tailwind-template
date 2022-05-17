<Tailwindcss />
<script lang="ts">
	import Tailwindcss from "./Tailwindcss.svelte";
	import "../node_modules/bulma/css/bulma.css";
	import Theme from "./utils/Theme.svelte";
	let themeComponent:Theme;
	let theme: "dark" | "light";

	let newTheme: string;
	let themeError: string = "";
</script>
<Theme bind:this={themeComponent} bind:theme />
<main>
	<body class="dark:bg-gray-700">
		<h1 class="text-red-600">{themeError}</h1>
		<h1 class="dark:text-white">Enter Your Theme(dark or light) Current: {theme} will be applied {(newTheme=="light" || newTheme=="dark")? newTheme: "nothing"}</h1>
		<input bind:value={newTheme} />
		<button
			on:click={() => {
				if (newTheme=="dark" || newTheme=="light") {
					themeComponent.changeTheme(newTheme);
					themeError = "";
				} else {
					themeError = "Please enter a valid theme";
				}
			}}
			class="box hover:!bg-red-700 !bg-yellow-100 dark:!bg-gray-400"
		>
			Apply
		</button>
	</body>
</main>

<style style="scss">
</style>
