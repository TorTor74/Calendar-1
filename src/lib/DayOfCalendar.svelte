<script>
	import { format } from "date-fns";
	import DayOfWeek from "./DayOfWeek.svelte";
	import TimeLine from "./TimeLine.svelte";
	import Line from "./Line.svelte";
    import { getContext } from "svelte";
	const today = new Date();
	const day=getContext('today')
	// const day = new Date();
</script>

<div class="day">
	<div class="header">
		<div class="dateDay">
			<b>{format($day, "d MMMM")}</b>
			<span>{format($day, "yyyy")}<b>г.</b></span>
		</div>
		<div class="dateWeek">
			{format($day, "EEEE")}
		</div>
	</div>
	<div class="time">
		<TimeLine />
		<DayOfWeek day={$day} {today} />
		<Line />
	</div>
</div>

<style lang="scss">
	.day {
		width: 869px;
		flex-shrink: 0;
		padding: 4px 0 0 16px;
	}
	.header {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: start;
		border-bottom: 1px solid #e5e5e5;

		.dateDay {
			color: #000;
			text-align: right;
			font-family: Helvetica;
			font-size: 26px;
			font-style: normal;
			line-height: normal;
		}
		.dateWeek {
			color: #000;
			text-align: right;
			font-family: Helvetica;
			font-size: 16px;
			font-style: normal;
			font-weight: 400;
			line-height: normal;
		}
	}
	.time {
		display: flex;
		width: 100%;
		position: relative;
		:global(.item) {
			display: flex;
			flex-direction: column;
			align-items: flex-start;
			flex-shrink: 0;
			:global(.hours){
				width: 764px;
				border-top:3px solid #EDEDED;
			}
			:global(.allDay){
				border: unset;
			}
		}
	}
</style>
