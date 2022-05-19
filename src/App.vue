<template>
  <body>
    <div id="app">
      <div class="top">
        <h1 class="title">{{ title }}</h1>
        <h2 class="date">{{ currentDateTime() }}</h2>
      </div>

      <ul v-if="entries" class="main">
        <li class="bloque" v-for="entry in entries" :key="entry.id">
          <span class="date-box"
            >{{ entry[0] }} - {{ entry[1].replaceAll("/", ".") }}</span
          >
          <span class="tittle-box">{{ entry[2] }}</span>
          <span class="description-box">{{ entry[3] }}</span>
        </li>
      </ul>

      <div v-else class="notWorking">
        <p class="title" >{{ notWorking }}</p>
        <img  class="imgNotWorking" src="./assets/notWorking.png" />
      </div>

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
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      title: "Welcome to Opportunity",
      sheet_id: "1a81aI0Y8ViZO0tI92h2YSMqVQJ8hmNNMyMylXgvwiU4",
      api_token: "AIzaSyA-qeDXOhEeQDA0vQf7LgkF7DQtGnAtmAU",
      entries: [],
      notWorking: "Please come back later"
    };
  },

  computed: {
    gsheet_url() {
      return `https://sheets.googleapis.com/v4/spreadsheets/${this.sheet_id}/values:batchGet?ranges=A2%3AE100&valueRenderOption=FORMATTED_VALUE&key=${this.api_token}`; //HERE I CHANGED THE STARTING LINE IN ORDER TO NOT SEE THE TITLES IN THE INFO OF THE ARRAY
    },
  },

  methods: {
   
    currentDateTime() {
          const current = new Date();
          const dia = current.getDate();
          const mes = current.getMonth() + 1;
          const year = current.getFullYear();
          const dateTime = dia + "." + mes + "." + year;
          if (mes < 10) {
            return dia + "." + "0" + mes + "." + year;
          }
          return dateTime;
        },

    getData() {
      axios.get(this.gsheet_url).then((response) => {
        this.entries = response.data.valueRanges[0].values;
      });
    },

    refreshData() {
      this.currentDateTime();
      this.getData()
    },
  },

  mounted() {
    this.refreshData();
    setInterval (this.refreshData, 1000 * 60 * 30);
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;900&display=swap");

/* LAYOUT */
#app {
  background-color: #e6eff4;
  font-family: "Inter", sans-serif, arial;
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
.imgNotWorking{
  padding: 1rem;
  width: auto;
  height: 25vh;
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
