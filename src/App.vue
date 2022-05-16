<template>
  <div id="app">
    <div class="page">
      <div class="top">
        <h1 class="title">Welcome to Opportunity</h1>
        <h2 class="date">{{ currentDateTime() }}</h2>
      </div>

      <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->

      <ul class="main">
        <li class="bloque">
          <h3 class="date-box">14.00 Uhr</h3>
          <h3 class="tittle-box">Basisbeschäftigung Besuch</h3>
          <h3 class="description-box">
            Interessierte für zweiten Kurs werden uns besuchen
          </h3>
        </li>

        <li class="bloque">
          <h3 class="date-box">14.00 Uhr</h3>
          <h3 class="tittle-box">Basisbeschäftigung Besuch</h3>
          <h3 class="description-box">
            Interessierte für zweiten Kurs werden uns besuchen
          </h3>
        </li>

        <li class="bloque">
          <h3 class="date-box">14.00 Uhr</h3>
          <h3 class="tittle-box">Basisbeschäftigung Besuch</h3>
          <h3 class="description-box">
            Interessierte für zweiten Kurs werden uns besuchen
          </h3>
        </li>
      </ul>
    </div>

    <footer>
      <img class="img-footer" alt="stadt zürich logo" src="./assets/STZH_SEB_Logo.png"/>
      <img class="img-footer" alt="Opportunity logo"  src="./assets/Opportunity.png"/>
      <img class="img-footer" alt="Sag logo" src="./assets/SAG_Logo_De.png" />
    </footer>
  </div>
</template>

<script>
//Here could go import, to acces to different components.

export default {
  name: "App",
  components: {},

  methods: {
    currentDateTime() {
      const current = new Date();
      const dia = current.getDate();
      const mes = current.getMonth();
      const year = current.getFullYear();

      const dateTime = dia + "." + mes + "." + year;

      if (mes < 10) {
        return dia + "." + "0" + mes + "." + year;
      }
      return dateTime;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;900&display=swap");

#app {
  background-color: #e6eff4;
  font-family: "Inter", sans-serif;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  padding: 0;
}
.page {
  height: 95vh;
}
.title {
  font-size: 62px;
  font-weight: bold;
}
.date {
  color: #9aa7b1;
  font-size: 62px;
  font-weight: bold;
}

.main {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

.bloque {
  background-color: #0f05a0;
  display: flex;
  text-align: left;
  flex-direction: column;
  padding: 3rem;
  margin: 3rem;
}

footer {
  
  bottom: 0;  
  background-color:white;
  display: flex;
  justify-content: space-around;
  /* display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); */
}
.img-footer {
  padding: 1rem;
  width: auto;
  height: 3vh;
  object-fit: contain;
}

.date-box {
  color: #eb5e00;
  font-weight: bold;
}
.tittle-box {
  color: #ffbaab;
  font-weight: bold;
}
.description-box {
  color: #ffbaab;
}
.top {
  text-align: left;
  margin-left: 3rem;
  margin-right: 3rem;
  padding-top: 2rem;
}
</style>
