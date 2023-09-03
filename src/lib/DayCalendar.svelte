<script>
	import DayOfCalendar from "./DayOfCalendar.svelte";
	import DayOfYearNew from "./MonthOfYear.svelte";
</script>

<div class="container">
	<DayOfCalendar />
	<div class="month">
		<DayOfYearNew />
		<div class="event">Нет входящих событий</div>
	</div>
</div>

<style lang="scss">
	.container {
		display: flex;
		width: 100%;
		flex-shrink: 1;
		.month {
			background: #e5e6e7;
			:global(.dateMonth) {
				margin: 6px 13px 0 11px;
			}
			.event {
				display: flex;
				// width: 321px;
				height: 446px;
				align-items: center;
				justify-content: center;
				flex-shrink: 0;
				color: #a5a6a7;
				text-align: right;
				font-family: Helvetica;
				font-size: 16px;
				font-style: normal;
				font-weight: 400;
				line-height: normal;
			}
		}
	}
</style>
