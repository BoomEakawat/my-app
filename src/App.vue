<template>
  <section>
    <img :src="picture" :width="size" :height="size" ref="imageEl"><br>

    <form @submit.prevent="submitForm">
      <label>input your nickname : </label>
      <input type="text" ref="nickNameEl">
      <button type="submit">submit</button>
    </form>
    <!-- input your nickname : <input type="text" v-on:input="setNickname"> -->
    <h1>{{ getFullname() }}</h1>
    <h1>Nickname: <span v-html="nickname"></span></h1>
    <p>ig : <a :href="ig" target="_blank">Instagram</a></p>
    <p>hobbies</p>
    <ul>
      <li>{{ hobbies[0] }}</li>
      <li>{{ hobbies[1] }}</li>
      <li>{{ hobbies[2] }}</li>
    </ul>
    <p>General Information:</p>
    <ul>
      <li>Gender: {{ general.gender }}</li>
      <li>Weight: {{ general.weight }} kg</li>
      <li>Height: {{ general.height }} cm</li>
      <li>Status: {{ general.status }}</li>
    </ul>
    <button @click="showData">Click here</button>
    <button @click.ctrl="increment(10)">+</button>
    <button @click.middle="decrement(5)">-</button>
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
      hobbies: ["Football", "Basketball", "Swimming"],
      general: {
        gender: "male",
        weight: 70,
        height: 180,
        status: "false"
      }
    }
  },
  methods: {
    getFullname() {
      return `${this.firstname} ${this.lastname}, ${this.age} years old.`
    },
    showData() {
      alert(`Name: ${this.firstname}`)
    },
    increment(value) {
      this.age+=value
    },
    decrement(value) {
      this.age-=value
    },
    // setNickname(event) {
    //   this.nickname = event.target.value
    //   console.log(event.target.value);
    // },
    submitForm() {
      alert(`Your nickname is ${this.$refs.nickNameEl.value}`)
      console.log(this.$refs.nickNameEl.value);
      this.nickname = this.$refs.nickNameEl.value
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
