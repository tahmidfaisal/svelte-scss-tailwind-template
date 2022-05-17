<script lang="ts">
    type ThemeT = "dark" | "light";

    function _themeUpdated(theme: ThemeT) {
        if (theme == "dark") {
            document.documentElement.classList.add("dark");
        } else if (theme == "light") {
            document.documentElement.classList.remove("dark");
        } else console.log("Invalid theme");
    }
    // create a local storage theme variable and create functions to change theme to light, dark or default
    export let theme: ThemeT = localStorage.getItem("theme") as ThemeT;

    if (theme == null) {
        let newTheme: ThemeT;
        if (
            window.matchMedia &&
            window.matchMedia("(prefers-color-scheme: dark)").matches
        ) {
            newTheme = "dark";
        } else {
            newTheme = "light";
        }
        localStorage.setItem("theme", newTheme);
        _themeUpdated(newTheme);
        theme = newTheme;
    }

    _themeUpdated(theme);

    export function changeTheme(newTheme: ThemeT | "default") {
        if (newTheme == "default") {
            //get system theme
            if (
                window.matchMedia &&
                window.matchMedia("(prefers-color-scheme: dark)").matches
            ) {
                newTheme = "dark";
            } else {
                newTheme = "light";
            }
            return;
        } else if (newTheme == "dark" || newTheme == "light")
            localStorage.setItem("theme", newTheme);
        else console.log("Invalid theme");
        _themeUpdated(newTheme);
        theme = newTheme;
    }
</script>
