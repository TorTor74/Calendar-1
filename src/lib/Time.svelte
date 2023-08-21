<script>
    import { isWeekend } from "date-fns";
    export let days;
    export let time;
</script>

<div class="grid">
    {#each days as day}
        {#each time as t}
            <div class="item" class:weekend={isWeekend(day)}></div>
        {/each}
    {/each}
</div>

<style lang="scss">
    .grid {
        //     display: grid;
        //     grid-template-columns: repeat(7, 1fr);
        //   grid-template-rows: repeat(25, 1fr);
        //   justify-content: flex-end;
        //   align-items: flex-start;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        align-content: flex-start;
        gap: 1px;
        flex-shrink: 0;
        flex-wrap: wrap;
        width: 100%;
        height: calc(46px * 26);
        .item {
            width: calc(100% / 7);

            // width: 156px;
            height: 46px;
            flex-shrink: 0;
            border: 1px solid #d9d9d9;
            &.weekend {
                background: #f5f5f5;
                font-family: Helvetica;
                font-size: 16px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
            }
        }
    }
</style>
