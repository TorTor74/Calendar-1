<script>
	import { format, isSameDay, isWeekend, eachHourOfInterval, startOfDay, addHours } from "date-fns";
	import Time from "./Time.svelte";
	import { getContext } from "svelte";

	const isWeek = getContext("isWeek");

	export let day;
	export let today;

	const start = startOfDay(today);
	const end = addHours(start, 24);
	const times = eachHourOfInterval({ start, end });
</script>

<div class="item" class:weekend={isWeekend(day)}>
	{#if $isWeek}
		<div class="day">
			{format(day, "EEEEEE,")}

			<span class:today={isSameDay(day, today)}>{format(day, "d")}</span>
		</div>
	{/if}
	<div class="allDay" />
	<div class="hours">
		{#each times as hour}
			<Time />
		{/each}
	</div>
</div>

<style lang="scss">
	.item {
		&.weekend {
			.day {
				color: #808080;
				font-family: Helvetica;
				font-size: 16px;
				font-style: normal;
				font-weight: 400;
				line-height: normal;
			}
		}
		.allDay {
			height: 20px;
			border-top: unset;
			border: 1px solid #d9d9d9;
			border-bottom: 3px solid #d9d9d9;
			position: sticky;
			background: #fff;
			top:32px;
		}
		.day {
			display: flex;
			height: 32px;
			background: #fff;
			border-bottom: 1px solid #d9d9d9;
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
			position: sticky;
			top: 0px;

			span {
				flex-shrink: 0;
				display: flex;
				padding: 6px 5px 5px 6px;
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
	}
	:global(.item:first-child .hours .time) {
		border-left: none;
	}
</style>
