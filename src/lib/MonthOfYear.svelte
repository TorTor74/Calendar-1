<script>
	import {
		format,
		isSameDay,
		isSameMonth,
		eachDayOfInterval,
		startOfMonth,
		isWeekend,
		startOfWeek,
		addDays,
	} from "date-fns";

	import { getContext } from "svelte";

	const today = getContext("today");
	const selectedDay = getContext("selectedDay");
	let start = startOfWeek(startOfMonth($selectedDay));

	let end = addDays(start, 41);
	let days = eachDayOfInterval({ start, end });

	$: start = startOfWeek(startOfMonth($selectedDay));
	$: end = addDays(start, 41);
	$: days = eachDayOfInterval({ start, end });
</script>

<div class="dateMonth">
	<div class="days">
		<div class="day">Пн</div>
		<div class="day">Вт</div>
		<div class="day">Ср</div>
		<div class="day">Чт</div>
		<div class="day">Пт</div>
		<div class="day">Сб</div>
		<div class="day">Вс</div>
	</div>
	<div class="grid-calendar">
		{#each days as day}
			<div
				class="item"
				class:notNow={!isSameMonth(day, $selectedDay)}
				class:today={isSameDay(day, $today)}
				class:selected={isSameDay(day, $selectedDay)}
				class:weekend={isWeekend(day)}
				on:click={() => ($selectedDay = day)}
			>
				{format(day, "d")}
			</div>
		{/each}
	</div>
</div>

<style lang="scss">
	.dateMonth {
		max-width: 297px;
		display: flex;
		gap: 8px;
		justify-content: flex-start;
		align-items: baseline;
		flex-direction: column;
		position: sticky;
		top: 32px;
		background: #e5e6e7;
		
		header {
			flex-shrink: 0;
			color: #e84f42;
			font-family: "Helvetica";
			font-size: 19px;
			font-style: normal;
			font-weight: 400;
			line-height: normal;
			padding: 6px 10px;
			width: auto;
			height: auto;
		}
		.grid-calendar {
			grid-gap: 6px 22px;
			padding: 5px 8px 6px 8px;
			display: grid;
			grid-template-columns: repeat(7, 1fr);
			grid-template-rows: repeat(6, 1fr);
			justify-content: flex-end;
			align-items: flex-start;
			width: 100%;
			height: 100%;

			.item {
				display: flex;
				justify-content: center;
				align-items: center;
				align-content: center;
				flex-shrink: 0;
				flex-wrap: wrap;
				color: #272727;
				text-align: center;
				font-family: Helvetica;
				width: 21px;
				height: 21px;
				font-size: 13px;
				font-style: normal;
				font-weight: 400;
				line-height: normal;
				&.today {
					border-radius: 16px;
					color: #f00 !important;
				}
				&.selected {
					border-radius: 16px;
					background: #272727;
					color: #fff !important;
				}
				&.today &.selected {
					border-radius: 16px;
					background: #f00 !important;
					color: #fff !important;
				}
				&.notNow {
					color: #bdbdbd;
				}

				.month {
					padding-left: 5px;
					text-transform: lowercase;
				}
			}
			.weekend {
				color: #808080;
			}
		}
		.days {
			display: flex;
			width: 100%;
			height: 28px;
			padding: 8px 10px;
			align-items: center;
			gap: 28px;
			flex-shrink: 0;
			.day {
				color: #808080;
				font-family: "Helvetica";
				font-size: 13px;
				font-style: normal;
				font-weight: 400;
				line-height: normal;
			}
		}
	}
</style>
