<script>
	import { setDefaultOptions } from "date-fns";
	import Calendar from "./lib/Calendar.svelte";
	import WeekCalendar from "./lib/WeekCalendar.svelte";
	import YearCalendar from "./lib/YearCalendar.svelte";
	import { ru } from "date-fns/locale";
	import DayCalendar from "./lib/DayCalendar.svelte";
	import { setContext } from "svelte";
	import { writable } from "svelte/store";

	setDefaultOptions({ locale: ru, weekStartsOn: 1 });

	const today = writable(new Date());
	const selectedDay=writable(new Date());
	setContext("today", today);
	setContext("selectedDay",selectedDay)
</script>

<main>
	<!-- <YearCalendar/> -->
	<!-- <Calendar /> -->
	<!-- <WeekCalendar /> -->
	<DayCalendar />
</main>

<style>
	main {
		width: 100%;
		height: 100vh;
	}
</style>
