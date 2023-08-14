<script>
  import {format,isSameDay,isSameMonth, isToday} from "date-fns";
  import eachDayOfInterval from "date-fns/eachDayOfInterval";
  import startOfMonth from "date-fns/startOfMonth";
  import isWeekend from "date-fns/isWeekend";
  import isFirstDayOfMonth from "date-fns/isFirstDayOfMonth";
  import startOfWeek from "date-fns/startOfWeek";
  import { ru } from "date-fns/locale";
  import setDefaultOptions from "date-fns/setDefaultOptions";
  import addDays from "date-fns/addDays";
  import getMonth from 'date-fns/getMonth'
  import getDate from 'date-fns/getDate'

  setDefaultOptions({ locale: ru, weekStartsOn: 1 });
  //эьбгчжв умкичр

  const today = new Date(2023,0,1);
  let before = startOfWeek(startOfMonth(today));

  let last = addDays(before, 41);
  const days = eachDayOfInterval({
    start: before,
    end: last,
  });

</script>

<div class="container">
  <header>
    <b>{format(today, "LLLL")}</b>
    {format(today, "yyyy")}<b>г.</b>
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
        class:notNow={!isSameMonth(day,today)}
        class:today={isSameDay(day, today)}
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
  @font-face {
    font-family: "Helvetica";
    src: url("https://candyfonts.com/wp-data/2018/10/26/11538/HELR45W.ttf")
      format("woff");
  }
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
    .grid-calendar {
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      grid-template-rows: repeat(6, 1fr);
      justify-content: flex-end;
      align-items: flex-start;
      background: #bdbdbd;
      grid-gap: 1px;
      border: 1px solid #bdbdbd;
      width: 100%;
      height: 100%;
      .item {
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
        &.notNow {
          color: #bdbdbd;
          text-align: right;
          font-family: Helvetica;
          font-size: 16px;
          font-style: normal;
          font-weight: 400;
          line-height: normal;
        }
        &.today {
          color: #ff0000 !important;
          text-align: right;
          font-family: Helvetica;
          font-size: 16px;
          font-style: normal;
          font-weight: 400;
          line-height: normal;
        }
        .month {
          padding-left: 5px;
          text-transform: lowercase;
        }
      }
      .weekend {
        background: #F5F5F5;
        color: #7b7b7b;
        text-align: right;
        font-family: Helvetica;
        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
      }
    }
    .days {
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      grid-template-rows: 1fr;
      justify-items: end;
      align-items: end;
      width: 100%;
      height: auto;
      color: #272727;
      font-family: Helvetica;
      font-size: 16px;
      font-style: normal;
      font-weight: 400;
      line-height: normal;
      .day {
        padding: 0 10px;
      }
    }
  }
</style>
