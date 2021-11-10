<template>
  <div>
    <input
      type="number"
      placeholder="enter first number"
      v-model="firstNumber"
    />
    <br />
    <input
      type="number"
      placeholder="enter second number"
      v-model="secondNumber"
    />
    <br />
    <br />

    <button type="button" v-on:click="add('add')">ADD</button>
    <br />
    <button type="button" v-on:click="add('sub')">Subtract</button>
    <br />
    <button type="button" v-on:click="add('mul')">Multiplay</button>
    <br />
    <button type="button" v-on:click="add('divide')">Divide</button>
    <br />
    <div v-if="spinner === true">
      <loader></loader>
    </div>

  

    <div v-else-if="spinner === false">
      <div v-if= thirdNumber>
      {{ thirdNumber }}
      </div>
      <div v-else>
         0
        </div>

    </div>
    <div v-else></div>

    <br />
  </div>
</template>

<script>
import Loader from "./loader.vue";

export default {
  name: "HelloWorld",
  components: {
    Loader,
  },
  beforeCreate(){
  },
  created(){
  },
  data() {
    return {
      firstNumber: null,
      secondNumber: null,
      thirdNumber: null,
      spinner: null,
    };
  },


  methods: {
    add(value) {
      this.spinner = true;

      switch (value) {
        case "add":
          this.thirdNumber =
            parseInt(this.firstNumber) + parseInt(this.secondNumber);
          break;
        case "sub":
          this.thirdNumber =
            parseInt(this.firstNumber) - parseInt(this.secondNumber);
          break;
        case "mul":
          this.thirdNumber =
            parseInt(this.firstNumber) * parseInt(this.secondNumber);
          break;
        case "divide":
          this.thirdNumber =
            parseInt(this.firstNumber) / parseInt(this.secondNumber);
          break;
      }
      this.callFunction();
    },

    callFunction: function () {
      // this.spinner = null
      var v = this;
      setTimeout(function () {
        v.spinner = false;
      }, 3000);
    },
  },
  mounted() {
    // this.callFunction()
  },
  beforeUpdate(){
  },
  updated(){
  },
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input {
  width: 200px ;
  height :  40px
}
button{ 
height: 40px;
width: 80px
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
