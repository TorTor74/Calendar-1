<script>
	import DayOfYear from "./DayOfYear.svelte";
	import { addMonths, getYear, eachMonthOfInterval, startOfYear } from "date-fns";
    import { getContext } from "svelte";

	const today = getContext("today");
	let year = getYear($today);
	const start = startOfYear($today);
	const end = addMonths(start, 11);
	let months = eachMonthOfInterval({ start, end });
</script>

<div class="container">
	<header>{year}</header>
	<div class="grid-year">
		{#each months as month}
			<div class="moth">
				<DayOfYear {month} today={$today} />
			</div>
		{/each}
	</div>
</div>

<style lang="scss">
	.container {
		// width: 100vw;
		// height: 100vh;
		display: flex;
		justify-content: flex-start;
		align-items: baseline;
		flex-direction: column;

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
			width: auto;
			height: auto;
		}
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
	}
</style>
