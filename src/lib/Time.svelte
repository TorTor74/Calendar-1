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
        startOfHour,
        addHours,
        startOfMinute,
    } from "date-fns";
    export let days;
    export let time;
</script>

<div class="grid">
    {#each days as day}
        {#each time as t}
            <div class="item" />
        {/each}
    {/each}
</div>

<style lang="scss">
    .grid {
        display: flex;
        width: 1098px;
        height: 572px;
        align-items: flex-start;
        align-content: flex-start;
        gap: 1px;
        flex-shrink: 0;
        flex-wrap: wrap;
        .item {
            width: 156px;
            height: 46px;
            flex-shrink: 0;
            border: 1px solid #d9d9d9;
        }
    }
</style>
