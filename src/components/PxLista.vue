<template>
  <div class="flex_container">
    <div class="img-content">
      <img
        src="https://static.platzi.com/media/platzi-isotipo@2x.png"
        alt="icono de platzi"
      />
      <img
        class="text_platzi"
        src="https://static.platzi.com/media/logotipo-platzi.png"
        alt="texto platzi"
      />
    </div>
    <h1 class="tex-color">Mis Cursos de Platzi💚</h1>

    <p>
      <input
        v-model="title"
        class="input-custom"
        type="text"
        placeholder="Titulo del curso"
      />
    </p>
    <p>
      <input
        v-model="time"
        class="input-custom"
        type="number"
        placeholder="Horas"
      />
    </p>
    <p>
      <v-btn @click="addCourse" class="ma-2" color="success"
        >Guardar Curso
      </v-btn>
      <!-- <button class="tex-color button_custom">Guardar Curso</button> -->
    </p>

    <div class="div-center">
      <h3>Lista de Cursos</h3>
      <hr />
      <div class="red" v-show="show_messaje">
        <p>Aun no has realizado cursos</p>
      </div>
      <div v-show="show_courses">
        <ol v-for="i in courses" :key="i.time">
          Curso:
          {{
            i.title
          }}
          | horas:
          {{
            i.time
          }}
          <!-- Lista de cursos -->
        </ol>
        <hr />
        <p>
          Llevo <strong>{{ totalTime }}</strong> horas aprendiendo en Platzi.
          <b>#NuncaParesDeAprender 💚</b>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "px-lista",

  data: () => ({
    title: "",
    time: "",
    courses: [],
    show_courses: false,
    show_messaje: true,
  }),
  methods: {
    addCourse() {
      this.courses.push({ title: this.title, time: this.time });
      this.show_courses = true;
      this.show_messaje = false;
    },
  },

  computed: {
    totalTime() {
      if (!this.courses.length) {
        // eslint-disable-next-line vue/no-side-effects-in-computed-properties
        this.show_messaje = true;
        return 0;
      }

      return this.courses.reduce((a, b) => a + parseInt(b.time), 0);
    },
  },
};
</script>

<style>
.flex_container {
  display: flex;
  flex-direction: column;
  gap: 0rem;
  align-items: center;
}
.div-center {
  text-align: center;
}

.tex-color {
  color: #98ca3f;
}

.img-content {
  display: flex;
}

.input-custom {
  padding: 0.5rem;
  border-radius: 2rem;
  background-color: white;
}

.button_custom {
  border-radius: 2rem;
  border-color: #98ca3f;
  background-color: #121f3d;
}

h3,
p,
ol {
  color: aliceblue;
}

.text_platzi {
  width: 100px;
}

#app {
  font-family: sans-serif;
  flex-direction: column;
  padding: 20px;
  min-height: 800px;
}

.green {
  color: seagreen;
}

.red {
  color: tomato;
}

.orange {
  color: orange;
}

.uppercase {
  text-transform: uppercase;
}

a {
  color: inherit;
  text-decoration: none;
}

img {
  height: 64px;
  width: 64px;
}

a:hover {
  text-decoration: underline;
}

ul li {
  margin-top: 5px;
}

button {
  padding: 10px;
}

.row {
  justify-content: space-around;
  display: flex !important;
  flex-direction: row !important;
}

span {
  cursor: pointer;
}
</style>
