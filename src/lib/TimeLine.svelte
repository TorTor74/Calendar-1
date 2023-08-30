<script>
    import { format, eachHourOfInterval, startOfDay, addHours } from "date-fns";

    const today = new Date();
    const start = startOfDay(today);
    const end = addHours(start, 24);
    const times = eachHourOfInterval({ start, end });
</script>

<div class="times">
    <div class="allDay">весь день</div>
    <div class="hours">
        {#each times as hour}
            <div class="hour">{format(hour, "HH:mm")}</div>
        {/each}
    </div>
</div>

<style lang="scss">
    .times {
        display: flex;
        width: 70px;
        // height: 572px;
        flex-direction: column;
        align-items: flex-end;
        flex-shrink: 0;
        position: sticky;
        left: 0;

        .allDay {
            // margin-top: 32px;
            color: #bdbdbd;
            text-align: right;
            font-family: Helvetica;
            font-size: 11px;
            font-style: normal;
            font-weight: 700;
            line-height: normal;
            display: flex;
            width: 70px;
            height: 20px;
            flex-direction: column;
            justify-content: space-evenly;
            align-items: flex-end;
            flex-shrink: 0;
            border-bottom: 3px solid #d9d9d9;
            border-top: 1px solid #d9d9d9;
            position: sticky;
            background: #fff;
            top:32px
        }
        .hours {
            padding: 39px 0px;
            display: flex;
            width: 70px;
            flex-direction: column;
            align-items: flex-end;
            gap: 34px;

            .hour {
                display: flex;
                width: 70px;
                height: 12px;
                padding-right: 3px;
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
</style>
