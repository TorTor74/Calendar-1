<script>
    import { Route, active } from "tinro";
    import Calendar from "./Calendar.svelte";
    import WeekCalendar from "./WeekCalendar.svelte";
    import YearCalendar from "./YearCalendar.svelte";
    import DayCalendar from "./DayCalendar.svelte";
</script>

<div class="container">
    <div class="header">
        <div class="navigate">
            <a class="item" use:active href="/day">День</a>
            <div class="line" />
            <a class="item" use:active href="/week">Неделя</a>
            <div class="line" />
            <a class="item" use:active href="/month">Месяц</a>
            <div class="line" />
            <a class="item" use:active href="/year">Год</a>
        </div>
    </div>
    <div class="content">
        <Route path="/" redirect="/day" />
        <Route path="/day"><DayCalendar /></Route>
        <Route path="/week"><WeekCalendar /></Route>
        <Route path="/month"><Calendar /></Route>
        <Route path="year"><YearCalendar /></Route>
    </div>
</div>

<style lang="scss">
    .container {
        display: flex;
        flex-direction: column;
        flex: 1;
        width: 100%;
        height: 100%;
        .header {
            height: 32px;
            display: flex;
            justify-content: center;
            align-items: center;
            background: #e5e6e7;
            position: sticky;
            top: 0;
            z-index: 20;
            .navigate {
                margin: 8px 0;
                border-radius: 3px;
                border: 1px solid #d8d9da;
                height: 16px;
                display: flex;
                justify-content: space-around;
                width: 214px;
                .item {
                    padding: 2px 11px;
                    color: #a5a6a7;
                    font-size: 11px;
                    font-family: "Helvetica";
                    text-decoration: none;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    border-radius: 3px;
                }
                :global(.active) {
                    background: #d9d9d9;
                    border-radius: 3px;
                }
                .line {
                    width: 1px;
                    height: 10px;
                    background: #d8d9da;
                    margin: 2px 0;
                }
            }
        }
        .content {
            // height: 100%;
            height: calc(100vh - 32px);

        }
    }
</style>
