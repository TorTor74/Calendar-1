<script>
    	import {
		format,
		getMinutes,
		getHours,
	} from "date-fns";
		import {getContext} from "svelte";

	const today = getContext("today");

</script>
<div class="timeline" style="--hour:{getHours($today)} ; --minutes:{getMinutes($today)}">
    <div class="time">
        {format($today, "HH:mm")}
    </div>
    <div class="line" />
</div>
<style lang="scss">
    .timeline {
			position: absolute;
			top: calc(46px / 60 * var(--minutes) + var(--hour) * 46px + 61px);
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
</style>