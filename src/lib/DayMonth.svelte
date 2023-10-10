<script>
	import {
		format,
		isSameDay,
		isSameMonth,
		eachDayOfInterval,
		startOfMonth,
		isWeekend,
		isFirstDayOfMonth,
		startOfWeek,
		addDays,
	} from "date-fns";
	import { getContext } from "svelte";
	export let month

	const today = getContext("today");

	const start = startOfWeek(startOfMonth(month));
	const end = addDays(start, 41);
	const days = eachDayOfInterval({ start, end });

</script>


	<div class="grid-calendar">
		{#each days as day}
			<div
				class="item"
				class:notNow={!isSameMonth(day, month)}
				class:today={isSameDay(day, $today)}
				class:weekend={isWeekend(day)}
			>
				{isFirstDayOfMonth(day) ? format(day, "d") + ` ` + format(day, "MMM") : format(day, "d")}
			</div>
		{/each}
	</div>

<style lang="scss">
	@font-face {
		font-family: "Helvetica";
		src: url("https://candyfonts.com/wp-data/2018/10/26/11538/HELR45W.ttf") format("woff");
	}
		.grid-calendar {
			display: grid;
			grid-template-columns: repeat(7, 1fr);
			grid-template-rows: repeat(6, 1fr);
			justify-content: flex-end;
			align-items: flex-start;
			background: #e5e5e5;
			grid-gap: 1px;
			border: 1px solid #c7c7cc;
			width: 100%;
			height: 100%;
			.item {
				background: #fff;
				padding: 6px 11px;
				width: -webkit-fill-available;
				height: -webkit-fill-available;
				color: #272727;
				text-align: right;
				font-family: Helvetica;
				font-size: 16px;
				font-style: normal;
				font-weight: 400;
				line-height: normal;
				&.notNow {
					color: #bdbdbd;
					text-align: right;
					font-family: Helvetica;
					font-size: 16px;
					font-style: normal;
					font-weight: 400;
					line-height: normal;
				}
				&.today {
					color: #ff0000 !important;
					text-align: right;
					font-family: Helvetica;
					font-size: 16px;
					font-style: normal;
					font-weight: 400;
					line-height: normal;
				}
				.month {
					padding-left: 5px;
					text-transform: lowercase;
				}
			}
			.weekend {
				background: #f5f5f5;
				color: #7b7b7b;
				text-align: right;
				font-family: Helvetica;
				font-size: 16px;
				font-style: normal;
				font-weight: 400;
				line-height: normal;
			}
		}
		.days {
			display: grid;
			grid-template-columns: repeat(7, 1fr);
			grid-template-rows: 1fr;
			justify-items: end;
			align-items: end;
			width: 100%;
			height: auto;
			color: #272727;
			font-family: Helvetica;
			font-size: 16px;
			font-style: normal;
			font-weight: 400;
			line-height: normal;
			.day {
				padding: 0 10px;
			}
		}

</style>
