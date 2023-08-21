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
    import Time from "./Time.svelte";

    const today = new Date();

    const start = startOfWeek(today);

    const end = addDays(start, 6);
    const days = eachDayOfInterval({ start, end });
    const times = eachHourOfInterval({
        start: startOfDay(today),
        end: addHours(startOfDay(today), 24),
    });
    console.log(today);
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
    <div class="head">
        <span class="first">Весь день</span>
        <span />
        <span />
        <span /><span /><span /><span /><span />
    </div>
    <div class="grid-time">
        <div class="times">
            {#each times as hour}
                <span>{format(startOfMinute(hour), "HH:00")}</span>
            {/each}
        </div>
        <div
            class="timeline"
            style="--hour:{getHours(today)} ; --minutes:{getMinutes(today)}"
        >
            <div class="time">
                {format(today, "HH:")}{format(today, "mm")}
            </div>
            <div class="line" />
        </div>
        <Time time={times} {days} />
    </div>
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
        align-items: center;
        gap: 1px;
        justify-content: space-evenly;
        flex-shrink: 0;

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
    }
    .flex-times {
        .head {
            display: flex;
            height: 20px;
            // gap: 6px;
            justify-content: space-evenly;
            flex-shrink: 0;
            border-bottom: 3px solid #d9d9d9;
            span {
                // width: 100%;
                //width: 156px;
                //height: 46px;
                flex-shrink: 0;
                width: calc(100% / 8 );
                border: 1px solid #d9d9d9;
                &.first {
                    display: flex;
                    width: 70px;
                    height: 20px;
                    flex-direction: column;
                    justify-content: center;
                    flex-shrink: 0;
                    color: #bdbdbd;
                    text-align: right;
                    font-family: Helvetica;
                    font-size: 11px;
                    font-style: normal;
                    font-weight: 700;
                    line-height: normal;
                }
            }
        }
        .grid-time {
            display: flex;
            position: relative;
            .times {
                display: flex;
                width: 70px;
                height: 572px;
                padding: 39px 0px;
                flex-direction: column;
                align-items: flex-end;
                gap: 34px;
                flex-shrink: 0;

                span {
                    display: flex;
                    width: 70px;
                    height: 13px;
                    flex-direction: column;
                    justify-content: center;
                    flex-shrink: 0;
                    color: #bdbdbd;
                    text-align: right;
                    font-family: Helvetica;
                    font-size: 11px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                }
            }
        }
        .timeline {
            position: absolute;
            top: calc(46px / 60 * var(--minutes) + var(--hour) * 46px + 39px);
            display: flex;
            width: 100%;
            justify-content: center;
            align-items: center;
            gap: 6px;
            .time {
                display: flex;
                width: 70px;
                height: 13px;
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
