<script>
	import { format } from "date-fns";
	import DayOfWeek from "./DayOfWeek.svelte";
	import TimeLine from "./TimeLine.svelte";
	import Line from "./Line.svelte";
    import { getContext } from "svelte";
	//const today = new Date();
	const day=getContext('selectedDay')
	const today=getContext('today')
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
		<DayOfWeek day={$day} today={$today} />
		<Line />
	</div>
</div>

<style lang="scss">
	.day {
		width: 869px;
		flex-shrink: 0;
		padding: 0 0 0 12px;
	}
	.header {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: start;
		padding: 4px 0 6px;

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
			width: 764px;


			:global(.hours){
				width: 100%;
				
				:global(.time){
					border-left: unset;
				border-right: unset;
				}
			}
			
			:global(.allDay){
				border: unset;
				height: 20px;
				border-bottom: 3px solid #D9D9D9;
				border-top: 1px solid #D9D9D9;
				width: 100%;
			}
		}
	}
</style>
