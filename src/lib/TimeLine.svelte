<script>
     import {
        format,
        eachHourOfInterval,
        startOfDay,
        addHours,
        startOfMinute,
    } from "date-fns";

    const today = new Date();

    const times = eachHourOfInterval({
        start: startOfDay(today),
        end: addHours(startOfDay(today), 24),
    });
</script>
<div class="times">
    <span>весь день</span>
    {#each times as hour}
        <span>{format(startOfMinute(hour), "HH:00")}</span>
    {/each}
</div>
<style lang="scss">
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
                    height: 12px;
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
</style>