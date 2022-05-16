<template>
  <body>
    <div id="app">
      <div class="top">
        <h1 class="title">Welcome to Opportunity</h1>
        <h2 class="date">{{ currentDateTime() }}</h2>
      </div>
      <ul class="main">
        <li class="bloque">
          <span class="date-box">{{ time }}</span>
          <span class="tittle-box">{{ title }}</span>
          <span class="description-box">{{ description }}</span>
        </li>
        <li class="bloque">
          <span class="date-box">{{ time }}</span>
          <span class="tittle-box">{{ title }}</span>
          <span class="description-box">{{ description }}</span>
        </li>
        <li class="bloque">
          <span class="date-box">{{ time }}</span>
          <span class="tittle-box">{{ title }}</span>
          <span class="description-box">{{ description }}</span>
        </li>
      </ul>
      <footer>
        <img
          class="img-footer"
          alt="stadt zürich logo"
          src="./assets/STZH_SEB_Logo.png"
        />
        <img
          class="img-footer"
          alt="Opportunity logo"
          src="./assets/Opportunity.png"
        />
        <img class="img-footer" alt="Sag logo" src="./assets/SAG_Logo_De.png" />
      </footer>
    </div>
  </body>
</template>

<script>
//Here also could go import, to acces to different components.

export default {
  name: "App",
  data() {
    return {
      time: "14:00 Uhr",
      title: "Basisbeschäftigung Besuch",
      description: "Interessierte für zweiten Kurs werden uns besuchen",
    };
  },

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

/* LAYOUT */
#app {
  background-color: #e6eff4;
  font-family: "Inter", sans-serif;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  padding: 0;
}
/* DIV FOR HEADER */
.top {
  text-align: left;
  margin-left: 3rem;
  margin-right: 3rem;
  padding-top: 2rem;
}
.title {
  font-size: 62px;
  font-weight: 900;
}
.date {
  color: #9aa7b1;
  font-size: 62px;
  font-weight: 500;
}

/* MAIN CONTENT */
.main {
  list-style-type: none;
  margin: 0;
  padding: 0;
  height: 80vh;
  width: 100%;
}
.bloque {
  background-color: #0f05a0;
  display: flex;
  text-align: left;
  flex-direction: column;
  padding: 2rem;
  margin: 3rem;
}

/* TEXT OF BOXES */
.date-box {
  color: #eb5e00;
  font-weight: 900;
  font-size: 28px;
  line-height: 36px;
}
.tittle-box {
  color: #ffbaab;
  font-weight: 900;
  font-size: 28px;
  line-height: 36px;
}
.description-box {
  color: #ffbaab;
  font-size: 28px;
}

/* FOOTER */
footer {
  position: fixed;
  bottom: 0;
  width: 100vw;
  background-color: rgb(255, 255, 255);
  display: flex;
  justify-content: space-around;
  /* display: grid;  height: 95vh;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); */
}
.img-footer {
  padding: 2rem;
  width: auto;
  height: 3vh;
  object-fit: contain;
  align-items: center;
}

/* RESPONSIVE */

@media screen and (max-width: 600px) {
  body {
    background-color: #e6eff4;
    color: white;
  }
  .title {
    font-size: 30px;
    font-weight: 900;
  }
  .tittle-box {
    color: #ffbaab;
    font-weight: 900;
    font-size: 20px;
    line-height: 36px;
  }
  .date {
    color: #9aa7b1;
    font-size: 20px;
    font-weight: 500;
  }
  .img-footer {
    padding: 1rem;
    width: auto;
    height: 2vh;
    object-fit: contain;
    align-items: center;
  }
  footer {
    width: 100%;
    position: fixed;
    bottom: 0px;
    left: 0px;
    background-color: rgb(255, 255, 255);
  }
}
</style>
