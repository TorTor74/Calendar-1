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
        startOfMinute
    } from "date-fns";
    import Time from "./Time.svelte";

    const today = new Date(1998, 5, 17);

    const start = startOfWeek(today);

    const end = addDays(start, 6);
    const days = eachDayOfInterval({ start, end });
    const times = eachHourOfInterval({
        start: startOfHour(today),
        end: addHours(startOfHour(today), 24),
    });
</script>

<header>
    <header>
        <b>{format(today, "LLLL")}</b>
        {format(today, "yyyy")}<b>г.</b>
    </header>
</header>
<div class="days">
    {#each days as day}
        <div
            class="item"
            class:notNow={!isSameMonth(day, today)}
            class:weekend={isWeekend(day)}
        >
            {format(day, "EEEEEE,")}

            <span class:today={isSameDay(day, today)}>{format(day, "d")}</span>
        </div>
    {/each}
</div>
<div class="flex-times">
    <div class="times">
        {#each times as hour}
    <span>{format(startOfMinute(hour), "HH:MM")}</span>  
        {/each}
    </div>
    <Time />
</div>

<style lang="scss">
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
    }
    .days {
        display: flex;
        padding: 0px 0px 0px 76px;
        .item {
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

            flex-shrink: 0;
            &.notNow {
                color: #bdbdbd;
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
    }
    .flex-times{
        .times{
display: flex;
width: 70px;
height: 572px;
padding: 39px 0px;
flex-direction: column;
align-items: flex-end;
gap: 34px;
flex-shrink: 0;

        }
    }
</style>
