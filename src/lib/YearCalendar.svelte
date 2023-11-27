<script>
	import YearMothsCalendar from "./YearMothsCalendar.svelte";
	import { addMonths, getYear, eachMonthOfInterval, eachYearOfInterval, startOfYear } from "date-fns";
	import { getContext } from "svelte";
	import VirtualScroll from "svelte-virtual-scroll-list";

	const today = getContext("today");
	const start = getContext("start");
	const end = getContext("end");
	// const start = startOfWeek($today);

	let years = eachYearOfInterval({ start: $start, end: $end });
	let items = years.map((obj, i) => ({ obj }));
	let itemIndex=getYear($today)-getYear($start)
</script>

<VirtualScroll data={items} start={94} key="obj"keeps={10}  let:data let:index>
	<div class="container">
		<header>{getYear(data.obj)}</header>

		<YearMothsCalendar year={data.obj} />
	</div>
</VirtualScroll>

<style lang="scss">
	.container {
		// width: 100vw;
		// height: 100vh;
		display: flex;
		justify-content: flex-start;
		align-items: baseline;
		flex-direction: column;
		position: relative;

		header {
			flex-shrink: 0;
			color: #272727;
			font-family: Helvetica;
			font-size: 31px;
			font-style: normal;
			line-height: normal;
			text-transform: lowercase;
			text-align: start;
			padding: 10px 14px;
			width: 100%;
			height: auto;
			position: sticky;
			background: #fff;
			top:0;
		}
	}
</style>
