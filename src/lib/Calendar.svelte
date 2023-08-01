<script>
  let count = 0;
</script>

<div class="container">
  <header>сентябрь</header>
  <div class="days">
    <div class="day">Пн</div>
    <div class="day">Вт</div>
    <div class="day">Ср</div>
    <div class="day">Чт</div>
    <div class="day">Пт</div>
    <div class="day">Сб</div>
    <div class="day">Вс</div>
 
    <div class="item" />
  </div>
</div>

<style lang="scss">
  .container {
    width: 100%;
    height: 100%;
    // display: flex;
    // justify-content: flex-start;
    // align-items: baseline;
    // flex-direction: column;
    // display: grid;
    //  grid-template-columns: repeat(7,1fr);
    //  grid-template-rows: 50px 150px repeat(6,1fr);
    
    header{
    //   grid-column-start: 1;
    // grid-column-end: 8;
    }
    .days{
    display: grid;
    grid-template-columns: repeat(7,1fr);
     grid-template-rows: repeat(7,1fr);
    }
    .grid-calendar{
  
  
    }
  }
</style>
