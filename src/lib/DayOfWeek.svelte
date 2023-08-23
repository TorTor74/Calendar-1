<script>
	import {
		format,
		isSameDay,
		isSameMonth,
		isWeekend,
		eachHourOfInterval,
		startOfDay,
		addHours,
	} from "date-fns";
    import Time from "./Time.svelte";

	export let day;
	export let today;
	const times = eachHourOfInterval({
		start: startOfDay(today),
		end: addHours(startOfDay(today), 24),
	});
</script>

<div class="item">
	<div
		class="day"
		class:notNow={!isSameMonth(day, today)}
		class:weekend={isWeekend(day)}
	>
		{format(day, "EEEEEE,")}

		<span class:today={isSameDay(day, today)}>{format(day, "d")}</span>
	</div>
	<div class="allDay"></div>
	<div class="hours">
		{#each times as hour }
			<Time/>
		{/each}
	</div>
</div>

<style lang="scss">
	.item {
		height: 100%;
		width: calc(100%/7);
		.allDay{
			height: 20px;
			border: 1px solid #D9D9D9;
			border-bottom: 3px solid #D9D9D9;
		}
	}
	.day {
	
		display: flex;
		height: 32px;
		justify-content: center;
		align-items: center;
		flex-shrink: 0;
		color: #272727;
		font-family: Helvetica;
		font-size: 16px;
		font-style: normal;
		font-weight: 400;
		line-height: normal;
		gap: 2px;
		text-transform: capitalize;

		flex-shrink: 0;
		&.notNow {
			color: #bdbdbd;
		}
		&.weekend {
			color: #808080;
			font-family: Helvetica;
			font-size: 16px;
			font-style: normal;
			font-weight: 400;
			line-height: normal;
		}
		span {
			flex-shrink: 0;

			display: flex;
			padding: 6px 7px 7px 7px;
			justify-content: center;
			align-items: center;
		}
		.today {
			border-radius: 16px;
			background: #f00;
			color: #fff !important;
		}
		.month {
			padding-left: 5px;
			text-transform: lowercase;
		}
	}
</style>
