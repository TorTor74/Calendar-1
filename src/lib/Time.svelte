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
            <div class="item"         
            class:weekend={isWeekend(day)}
            />
        {/each}
    {/each}
</div>

<style lang="scss">
    .grid {
        display: grid;
        grid-template-columns: repeat(7, 1fr);
      grid-template-rows: repeat(25, 1fr);
      justify-content: flex-end;
      align-items: flex-start;
      width: 100%;
      height: 100%;
        .item {
            
            // width: 156px;
            height: 46px;
            flex-shrink: 0;
            border: 1px solid #d9d9d9;
            &.weekend{
                background: #F5F5F5;
                font-family: Helvetica;
font-size: 16px;
font-style: normal;
font-weight: 400;
line-height: normal;  
            }
        }
    }
</style>
