<script>
    import { setDefaultOptions } from 'date-fns';
  import Calendar from './lib/Calendar.svelte'
    import WeekCalendar from './lib/WeekCalendar.svelte';
  import YearCalendar from './lib/YearCalendar.svelte';
  import { ru } from "date-fns/locale";

setDefaultOptions({ locale: ru, weekStartsOn: 1 });
</script>

<main>
  <!-- <YearCalendar/> -->
    <!-- <Calendar /> -->
    <WeekCalendar/>
</main>

<style>
main{
  width: 100vw;
  height: 100vh;
}
</style>
