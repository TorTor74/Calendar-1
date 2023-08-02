<script>
  import { formatDistance, subDays, format } from "date-fns";
  import getDaysInMonth from "date-fns/getDaysInMonth";
  import eachDayOfInterval from "date-fns/eachDayOfInterval";
  import startOfMonth from "date-fns/startOfMonth";
  import endOfMonth from "date-fns/endOfMonth";
  import getDay from "date-fns/getDay";
  import subMonths from "date-fns/subMonths";
  import addMonths from "date-fns/addMonths";
  import addDays from "date-fns/addDays";
  import lastDayOfMonth from "date-fns/lastDayOfMonth";

  formatDistance(subDays(new Date(), 3), new Date(), { addSuffix: true });
  const today = new Date();
  let startMonth = getDay(startOfMonth(today));
  let before =
    startMonth == 0 ? startOfMonth(today) : subDays(today, startMonth);
  let endDays = 14 - getDay(endOfMonth(today));

  let last =
    endDays == 0 ? endOfMonth(today) : addDays(lastDayOfMonth(today), endDays);
  const days = eachDayOfInterval({
    start: before,
    end: last,
  });

  console.log(days);
</script>

<div class="container">
  <header>
    <b>{format(today, "MMMM")}</b>
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
        class:notNow={format(day, "MMM") != format(today, "MMM")}
        class:today={format(day, 'MM dd yyyy')==format(today, 'MM dd yyyy')}
      >
        {#if format(day, "dd") == "01"}
          {format(day, "d")}<span class="month">{format(day, "MMM")}.</span>
        {:else}
          {format(day, "d")}
        {/if}
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
      background: #BDBDBD;
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
        &.today{
          color: #ff0000;
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
      .item:nth-child(7n + 6),
      .item:nth-child(7n + 7) {
        background: #ccc;
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
