<script>
	import {
		format,
		startOfWeek,
		addDays,
		eachDayOfInterval,
		isSameDay,
		isSameMonth,
		isWeekend,
		eachHourOfInterval,
		startOfDay,
		addHours,
		startOfMinute,
		getMinutes,
		getHours,
	} from "date-fns";

	export let day;
	export let today;
</script>
<div class="item">
<div class="day" class:notNow={!isSameMonth(day, today)} class:weekend={isWeekend(day)}>
	{format(day, "EEEEEE,")}

	<span class:today={isSameDay(day, today)}>{format(day, "d")}</span>
</div>
</div>
<style lang="scss">
	.item{
        height: 100%;
        border-right: 1px solid #808080;
    }
		.day {
			display: flex;
			width: 156px;
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
