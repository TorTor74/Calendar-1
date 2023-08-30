<script>
	import { getContext } from "svelte";
	import DayOfCalendar from "./DayOfCalendar.svelte";
	import DayOfYear from "./DayOfYear.svelte";
	import { getMonth } from "date-fns";
	import DayOfYearNew from "./MonthOfYear.svelte";
	const today = getContext("today");
	const month = getMonth(today);
</script>

<div class="container">
	<DayOfCalendar />
	<div class="month">
		<DayOfYearNew />
		<div class="even">Нет входящих событий</div>
	</div>
</div>

<style lang="scss">
	.container {
		display: flex;
		width: 100%;
		.month {
			background: #e5e6e7;
			:global(.dateMonth){
				margin: 6px  13px 0 11px;
			}
			.even {
				display: flex;
				width: 321px;
				height: 446px;
				padding: 178px 68px 249px 68px;
				flex-direction: column;
				align-items: center;
				flex-shrink: 0;
				color: #A5A6A7;
text-align: right;
font-family: Helvetica ;
font-size: 16px;
font-style: normal;
font-weight: 400;
line-height: normal;
			}
		}
	}
</style>
