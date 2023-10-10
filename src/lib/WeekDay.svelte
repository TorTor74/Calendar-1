<script>
	import { format, startOfWeek, addDays, eachDayOfInterval, getMinutes, getHours } from "date-fns";
	import TimeLine from "./TimeLine.svelte";
	import DayOfWeek from "./DayOfWeek.svelte";
	import { getContext } from "svelte";
	import VirtualScroll from "svelte-virtual-scroll-list";

	export let day

	const start = day;

	const end = addDays(start, 6);
	const days = eachDayOfInterval({ start, end });
	const isWeek = true;

</script>



	<div class="days">
			{#each days as day}
				<DayOfWeek {day} {isWeek} />
			{/each}
	</div>

	

<style lang="scss">
	
		.days {
			align-items: center;
			justify-content: space-evenly;
			flex-shrink: 0;
			width: calc(100% - 70px);
			display: flex;
			scroll-snap-type: x mandatory;

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


</style>
