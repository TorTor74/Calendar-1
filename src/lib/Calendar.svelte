<script>
	import {
		format,
		isSameDay,
		isSameMonth,
		eachDayOfInterval,
		eachMonthOfInterval,
		startOfMonth,
		isWeekend,
		isFirstDayOfMonth,
		startOfWeek,
		addDays,
	} from "date-fns";
	import { getContext } from "svelte";
    import DayMonth from "./DayMonth.svelte";
	import VirtualScroll from "svelte-virtual-scroll-list";

	//эьбгчжв умкичр
	const start = getContext("start");
	const end = getContext("end");
	// const start = startOfWeek($today);

	let months = eachMonthOfInterval({ start: $start, end: $end });
	let items = months.map((obj, i) => ({ obj }));

	const today = getContext("today");


</script>
<VirtualScroll data={items}  start={15}	key="obj" let:data let:index>

<div class="container">
	<header>
		<b>{format(data.obj, "LLLL")}</b>
		{format(data.obj, "yyyy")}<b>г.</b>
	</header>
	<div class="days">
		<div class="day">Пн</div>
		<div class="day">Вт</div>
		<div class="day">Ср</div>
		<div class="day">Чт</div>
		<div class="day">Пт</div>
		<div class="day">Сб</div>
		<div class="day">Вс</div>
	</div>
	<DayMonth month={data.obj}/>
</div>
</VirtualScroll>

<style lang="scss">
	@font-face {
		font-family: "Helvetica";
		src: url("https://candyfonts.com/wp-data/2018/10/26/11538/HELR45W.ttf") format("woff");
	}
	.container {
		height: calc(100vh - 32px);
		display: flex;
		justify-content: flex-start;
		align-items: baseline;
		flex-direction: column;

		header {
			flex-shrink: 0;
			color: #272727;
			font-family: Helvetica;
			font-size: 32px;
			font-style: normal;
			line-height: normal;
			text-transform: lowercase;
			text-align: start;
			padding: 9px 14px;
			width: auto;
			height: auto;
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
	}
</style>
