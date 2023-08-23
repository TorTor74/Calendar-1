<script>
    import { isWeekend } from "date-fns";
</script>

    <div class="time"></div>

<style lang="scss">
   
        .time {
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
    
</style>
