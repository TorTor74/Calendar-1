<script>
    import { Route } from "tinro";
    import Calendar from "./Calendar.svelte";
    import WeekCalendar from "./WeekCalendar.svelte";
    import YearCalendar from "./YearCalendar.svelte";
    import DayCalendar from "./DayCalendar.svelte";
</script>

<div class="container">
    <div class="header">
        <div class="navigate">
            <a class="item" href="/day">День</a>
            <a class="item" href="/week">Неделя</a>
            <a class="item" href="/month">Месяц</a>
            <a class="item" href="/year">Год</a>
        </div>
    </div>
    <div class="content">
        <Route path="/day"><DayCalendar /></Route>
        <Route path="/week"><WeekCalendar /></Route>
        <Route path="/month"><Calendar /></Route>
        <Route path="year"><YearCalendar /></Route>
        <!-- <YearCalendar/> -->
        <!-- <Calendar /> -->
        <!-- <WeekCalendar /> -->
        <!-- <DayCalendar /> -->
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
            .navigate {
                border-radius: 3px;
                border: 1px solid #d8d9da;
                .item {
                    padding: 0 11px;
                    color: #a5a6a7;
                    font-size: 11px;
                    font-family: "Helvetica";
                    text-decoration: none;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                }
            }
        }
        .content {
            height: 100%;
        }
    }
</style>
