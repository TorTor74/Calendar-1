<script>
	import {
		format,
		startOfWeek,
		addDays,
		eachDayOfInterval,
		getMinutes,
		getHours,
		eachWeekOfInterval,
	} from "date-fns";
	import TimeLine from "./TimeLine.svelte";
	import DayOfWeek from "./DayOfWeek.svelte";
	import { getContext } from "svelte";
	import VirtualScroll from "svelte-virtual-scroll-list";
	import WeekDay from "./WeekDay.svelte";

	const isWeek = true;

	const today= getContext("today");

	const start = getContext("start");
	const end = getContext("end");
	// const start = startOfWeek($today);

	let days = eachDayOfInterval({ start: $start, end: $end });
	let items = days.map((obj, i) => ({ obj }));
</script>

<VirtualScroll data={items} key="obj" keeps={1} isHorizontal={true} let:data let:index>
	<div class="container">
		<header>
			<header>
				<b>{format(data.obj, "LLLL")}</b>
				{format(data.obj, "yyyy")}<b>г.</b>
			</header>
		</header>
		<div class="flex-times">
			<TimeLine />
			<WeekDay day={data.obj} />

			<div class="timeline" style="--hour:{getHours($today)} ; --minutes:{getMinutes($today)}">
				<div class="time">
					{format($today, "HH:mm")}
				</div>
				<div class="line" />
			</div>
		</div>
	</div>
</VirtualScroll>

<style lang="scss">
	.container{
		width:calc(100vw - 70px);
	}
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
		position: sticky;
		top: 32px;
		background: #fff;
		z-index: 20;
	}

	.flex-times {
		display: flex;
		position: relative;

		.days {
			align-items: center;
			justify-content: space-evenly;
			flex-shrink: 0;
			width: calc(100% - 70px);
			display: flex;
			:global(.item) {
				height: 100%;
				width: calc(100% / 7);
			}
			:global(.weekend .hours) {
				background: #f5f5f5;
				font-family: Helvetica;
				font-size: 16px;
				font-style: normal;
				font-weight: 400;
				line-height: normal;
			}

			.allDay {
				background: #f5f5f5;
			}
		}

		.grid-time {
			display: flex;
			position: relative;
		}
		:global(.times .allDay) {
			margin-top: 32px;
			position: sticky;
			top: 134px;
		}
		.timeline {
			position: absolute;
			top: calc(46px / 60 * var(--minutes) + var(--hour) * 46px + 91px);
			display: flex;
			width: 100%;
			justify-content: center;
			align-items: center;
			gap: 6px;

			.time {
				display: flex;
				width: 70px;
				height: 13px;
				padding-right: 3px;
				flex-direction: column;
				justify-content: center;
				flex-shrink: 0;
				color: #eb4e3e;
				text-align: right;
				font-family: Helvetica;
				font-size: 11px;
				font-style: normal;
				font-weight: 400;
				line-height: normal;
			}

			.line {
				width: 100%;
				height: 1px;
				background: #eb4e3e;
			}
		}
	}
</style>
