<template>
  <form @submit.prevent="handleSubmit">
    <lable>Email:</lable>
    <input type="email" required v-model="userEmail" />

    <lable>Password:</lable>
    <input type="password" required v-model="password" />
    <p v-if="passwordError">{{ passwordError }}</p>

    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Developer</option>
      <option value="designer">Designer</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup="addSkill" />

    <div v-for="item in skills" :key="item">
      <p @click="deleteItem2(item)">{{ item }}</p>
    </div>

    <div>
      <input type="checkbox" required v-model="terms" />
      <label>terms and conditions</label>
    </div>

    <button>Submit</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      userEmail: "nestor",
      password: "",
      role: "designer",
      terms: false,
      tempSkill: "",
      skills: [],
      passwordError: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }
        this.tempSkill = "";
      }
    },
    deleteItem(item) {
      let itemIndex = this.skills.indexOf(item);
      console.log(itemIndex);
      this.skills.splice(itemIndex, 1);
    },
    handleSubmit() {
      // validate PW with ternary opperator
      this.passwordError = this.password.length > 5 ? "" : "Password must be over 5 characters long";
      if (!this.passwordError) {
        console.log(`userEmail: ${this.email}`);
        console.log(`password: ${this.password}`);
        console.log(`role: ${this.role}`);
      }
    },
  },
};
</script>

<style></style>
