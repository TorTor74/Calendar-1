<script>
  import { format, isSameDay, isToday } from "date-fns";
  import eachDayOfInterval from "date-fns/eachDayOfInterval";
  import startOfMonth from "date-fns/startOfMonth";
  import isWeekend from "date-fns/isWeekend";
  import isFirstDayOfMonth from "date-fns/isFirstDayOfMonth";
  import startOfWeek from "date-fns/startOfWeek";
  import { ru } from "date-fns/locale";
  import setDefaultOptions from "date-fns/setDefaultOptions";
  import addDays from "date-fns/addDays";
  import getMonth from "date-fns/getMonth";
  import getDate from "date-fns/getDate";

  setDefaultOptions({ locale: ru, weekStartsOn: 1 });
  //эьбгчжв умкичр

  export let month;
  export let today;

  let before = startOfWeek(startOfMonth(month));

  let last = addDays(before, 41);
  const days = eachDayOfInterval({
    start: before,
    end: last,
  });
</script>

<div class="container">
  <header>
    {format(month, "LLLL")}
  </header>
  <div class="days">
    <div class="day">Пн</div>
    <div class="day">Вт</div>
    <div class="day">Ср</div>
    <div class="day">Чт</div>
    <div class="day">Пт</div>
    <div class="day">Сб</div>
    <div class="day">Вс</div>
  </div>
  <div class="grid-calendar">
    {#each days as day}
      <div
        class="item"
        class:notNow={getMonth(day) != getMonth(month)}
        class:today={isSameDay(day, today)}
        class:weekend={isWeekend(day)}
      >
        {format(day, "d")}
      </div>
    {/each}
  </div>
</div>

<style lang="scss">
  .container {
    max-width: 297px;
    display: flex;
    gap: 8px;
    justify-content: flex-start;
    align-items: baseline;
    flex-direction: column;

    header {
      flex-shrink: 0;
      color: #e84f42;
      font-family: "Helvetica";
      font-size: 19px;
      font-style: normal;
      font-weight: 400;
      line-height: normal;
      padding: 6px 10px;
      width: auto;
      height: auto;
    }
    .grid-calendar {
      grid-gap: 6px 28px;
      padding: 5px 8px 6px 8px;
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      grid-template-rows: repeat(6, 1fr);
      justify-content: flex-end;
      align-items: flex-start;
      width: 100%;
      height: 100%;
      .item {
        display: flex;
        justify-content: center;
        align-items: center;
        align-content: center;
        flex-shrink: 0;
        flex-wrap: wrap;
        color: #272727;
        text-align: center;
        font-family: Helvetica;
        font-size: 13px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
        &.notNow {
          color: #bdbdbd;
        }
        &.today {
          border-radius: 16px;
          background: #F00;
          color: #fff !important;
        }
        .month {
          padding-left: 5px;
          text-transform: lowercase;
        }
      }
      .weekend {
        color: #808080;
      }
    }
    .days {
      display: flex;
      width: 100%;
      height: 28px;
      padding: 8px 10px;
      align-items: center;
      gap: 28px;
      flex-shrink: 0;
      .day {
        color: #808080;
        font-family: "Helvetica";
        font-size: 13px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
      }
    }
  }
</style>
