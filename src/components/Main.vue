<script>
import { Component, Vue } from "vue-property-decorator";// FOR USED #npm i -S vue-property-decorator #manualhttps://www.npmjs.com/package/vue-property-decorator
@Component
export default class Main extends Vue {
  checked(name, second_name, phone_number, age, gender,check_word) {
    return name && second_name && phone_number && age && gender && check_word;
  }
  check = false;
  first_name = "";
  second_name  = "";
  number = "";
  age = null;
  gender = "";
  validator_word = /[A-Z-a-z]/;
  month = null;
  //now = new Date().getMonth() + 1;
  secret_word = "2020"
  //check_word = ""

  captcha(check_word) {
    return this.secret_word === check_word;
  }
  name(name) {
    if (name !== "" && name.length < 30) {
        for (let i = 0; i < name.length; i++) {
          if (!this.validator_word.test(name[i])) {
            return false;
          }
        }
        return true;
    }else return false;
  }
  phone_number(number) {
    if (number.length === 11 && (number[0] === "8" || number[0] === "7")){
      return true;
    }
  }
  years(age) {
    return age < 100 && age > 0;
  }
  choice(gender) {
    return gender !== "";
  }
}
</script>

<template>
  <div class="Main">
    <h1>Tinder</h1>
    <div class="gender">
      <label>
        <input type="radio" v-model="gender" value="Female"/>
      </label>
      <label>Female</label>
      <label>
        <input type="radio" v-model="gender" value="Male"/>
      </label>
      <label>Male</label>
      <label>
        <input type="radio" v-model="gender" value="Animal"/>
      </label>
      <label>Animal</label>
    </div>
    <div class="text_in">
      <label>
        <input type="text" placeholder="Name ENG < 30" v-model="first_name" class="Main"/>
      </label>
    </div>
    <div class="one">
      <label>
        <input type="text" placeholder="Second name ENG< 30" v-model="second_name" class="form_input"/>
      </label>
    </div>
    <div class="one">
      <label>
        <input type="number" placeholder="Age < 100" v-model="age" class="form_input"/>
      </label>
    </div>
    <div class="one">
      <label>
        <input type="number" placeholder="Number (start 7 or 8, length 11)" v-model="number" class="form_input"/>
      </label>
    </div>
      <div class="one">
      <label>
        <input type="text" placeholder="NUMBER OF THIS YEAR?" v-model="month" class="form_input"/>
      </label>
    </div>
    <button type="submit" class="form_button" v-on:click="check = checked(name(first_name), name(second_name), phone_number(number), years(age), choice(gender),captcha(month))">Registration</button>
    <pre v-if="check">You are registered</pre>
  </div>
</template>


<style scoped>


.form_button {
  width: 100px;
  height: 35px;
  margin-top: 10px;
  border: none;
  border-radius: 5px;
  letter-spacing: 1px;
  color : #fff;
  background-color: #85a0be;
  outline: none;
  cursor: pointer;
  transition: 0.3s;
 }
button:not(:active) {
  transform: scale(1.0);
}
button:disabled {
  background-color: #679ed9;
}
h1 {
  margin-top: 0;
  margin-bottom: 0;
}
.error {
  border-color: red;
}
.error_input {
  color: red;
  font-size: small;
  padding-top: 10px;
}
</style>


