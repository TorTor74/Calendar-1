<script>
  import { format, isToday } from "date-fns";
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
  const today = new Date(2023, 0, 1);
  let before = startOfWeek(startOfMonth(month));

  let last = addDays(before, 41);
  const days = eachDayOfInterval({
    start: before,
    end: last,
  });
</script>

<div class="container">
  <header>
    <b>{format(month, "LLLL")}</b>
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
        class:today={getDate(day) == getDate(month) &&
          getMonth(day) == getMonth(month)}
        class:weekend={isWeekend(day)}
      >
        {isFirstDayOfMonth(day)
          ? format(day, "d") + ` ` + format(day, "MMM")
          : format(day, "d")}
      </div>
    {/each}
  </div>
</div>

<style lang="scss">
  .container {
    // width: 100vw;
    // height: 100vh;
    display: flex;
    gap: 8px;
    justify-content: flex-start;
    align-items: baseline;
    flex-direction: column;

    header {
      // height: 40px;
      flex-shrink: 0;
      color: #e84f42;
      font-family: Inter;
      font-size: 19px;
      font-style: normal;
      font-weight: 400;
      line-height: normal;
      padding: 6px 10px;
      width: auto;
      height: auto;

      //   grid-column-start: 1;
      // grid-column-end: 8;
    }
    .grid-calendar {
// width: 297px;
// height: 136px;
// padding: 5px 8px 6px 8px;
// align-items: flex-start;
// align-content: flex-start;
gap: 6px 28px;
// flex-shrink: 0;
// flex-wrap: wrap;
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      grid-template-rows: repeat(6, 1fr);
      justify-content: flex-end;
      align-items: flex-start;
      // background: #bdbdbd;
      // grid-gap: 1px;
      // border: 1px solid #bdbdbd;
      width: 100%;
      height: 100%;
      .item {
        color: #272727;
text-align: center;
font-family: Helvetica Neue;
font-size: 13px;
font-style: normal;
font-weight: 400;
line-height: normal;
        &.notNow {
          color: #bdbdbd;
        }
        &.today {
          color: #ff0000 !important;
        }
        .month {
          padding-left: 5px;
          text-transform: lowercase;
        }
      }
      .weekend {
        color: #7b7b7b;
      }
    }
    .days {
      display: flex;
      width: 297px;
      height: 28px;
      padding: 10px 8px;
      align-items: center;
      gap: 27px;
      flex-shrink: 0;
      .day {
        color: #808080;
        font-family: Inter;
        font-size: 13px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
      }
    }
  }
</style>
