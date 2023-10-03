<script>
	import { Route } from "tinro";
	import { setDefaultOptions } from "date-fns";
	import { ru } from "date-fns/locale";
	import { setContext } from "svelte";
	import { writable } from "svelte/store";
	import Layout from "./lib/layout.svelte";

	setDefaultOptions({ locale: ru, weekStartsOn: 1 });

	const today = writable(new Date());
	const selectedDay = writable(new Date());
	setContext("today", today);
	setContext("selectedDay", selectedDay);
</script>

<main>
	<Route>
		<Layout />
	</Route>
</main>

<style>
	main {
		width: 100%;
		height: 100vh;
	}
</style>
