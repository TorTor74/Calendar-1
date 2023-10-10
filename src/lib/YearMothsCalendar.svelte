<script>
	import DayOfYear from "./DayOfYear.svelte";
	import { addMonths, getYear, eachMonthOfInterval, eachYearOfInterval, startOfYear } from "date-fns";
	import { getContext } from "svelte";

	export let year;
	const start = startOfYear(year);
	const end = addMonths(start, 11);

	let months = eachMonthOfInterval({ start, end });
</script>

<div class="grid-year">
	{#each months as month}
		<div class="moth">
			<DayOfYear {month} />
		</div>
	{/each}
</div>

<style lang="scss">
	.grid-year {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		grid-template-rows: repeat(3, 1fr);
		justify-content: flex-end;
		align-items: flex-start;
		padding: 8px 46px;
		grid-gap: 8px 53px;
		width: 100%;
		height: 100%;
		.month {
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
		}
	}
</style>
