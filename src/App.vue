<template>
  <section>
    <img :src="picture" :width="size" :height="size" ref="imageEl"><br>
    <h1>{{ getFullname }}</h1>
    <h1>Salary: {{ salary }} Bath</h1>
    <h1>Annual salary: {{ getIncome }} Bath</h1>
    <h1>Position: {{ getPosition }}</h1>
    <button @click="salary += 5000">+</button>
    <button @click="salary -= 5000">-</button>
    <button @click="toggleInfo">{{ isVisible ? 'less' : 'more' }} info</button>
    <article v-show="isVisible">
      <p>ig : <a :href="ig" target="_blank">Instagram</a></p>
      <p v-if="hobbies.length === 0">no hobby</p>
      <div v-else>
        <p>Hobbies:</p>
        <ul>
          <li v-for="(item, index) in hobbies" :key="index">{{ item }}</li>
        </ul>
      </div>
      <p>General Information:</p>
      <ul>
        <li v-for="(item, key) in general" :key="key">{{ key }}: {{ item }}</li>
      </ul>
    </article>
  </section>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      firstname: "Eakawat",
      lastname: "Buanitisin",
      nickname: "",
      age: 20,
      picture: "https://www.w3schools.com/w3images/avatar2.png",
      size: 50,
      ig: "https://www.instagram.com/boom_eakawat/",
      hobbies: ["Football", "Basketball"],
      general: {
        gender: "male",
        weight: 70,
        height: 180,
        status: "false"
      },
      isVisible: false,
      salary: 200000,
    }
  },
  methods: {
    toggleInfo() {
      this.isVisible = !this.isVisible;
    },
    getRandomByMethods() {
      return Math.random();
    }
  },
  computed: {
    getFullname() {
      return `${this.firstname} ${this.lastname}, ${this.age} years old.`
    },
    getRandomByComputed() {
      return Math.random();
    },
    getIncome() {
      return this.salary * 12;
    },
    getPosition() {
      return this.salary >= 35000 ? "Senior" : "Junior";
    }
  },
  watch: {
    salary(value) {
      if (value > 50000) {
        this.salary = 50000;
        setTimeout(() => {
          alert("Salary cannot exceed 50000 Bath.");
        }, 2000);
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
