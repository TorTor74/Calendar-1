<script>
    import DayOfYear from "./DayOfYear.svelte";
    import { format, isToday, addMonths } from "date-fns";
    import getYear from "date-fns/getYear";
    import startOfYear from "date-fns/startOfYear";
    import eachMonthOfInterval from "date-fns/eachMonthOfInterval";

    const today = new Date(2023, 0, 1);
    let year = getYear(today);
    let months = eachMonthOfInterval({
        start: startOfYear(today),
        end: addMonths(startOfYear(today), 11),
    });
</script>

<div class="container">
    <header>{year}</header>
    <div class="grid-year">
        {#each months as month}
            <div class="moth">{month}
            <DayOfYear month={month}/>
        </div>
        {/each}
    </div>
</div>


<style lang="scss">
    .container {
        width: 100vw;
        height: 100vh;
        display: flex;
        justify-content: flex-start;
        align-items: baseline;
        flex-direction: column;

        header {
            // height: 40px;
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

            //   grid-column-start: 1;
            // grid-column-end: 8;
        }
        .grid-year {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            grid-template-rows: repeat(3, 1fr);
            justify-content: flex-end;
            align-items: flex-start;
            //background: #bdbdbd;
            grid-gap: 1px;
            border: 1px solid #bdbdbd;
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
