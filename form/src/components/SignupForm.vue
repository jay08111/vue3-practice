<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <label>Email : </label>
      <input type="email" required v-model="email" />
      <label>Password : </label>
      <input type="password" required v-model="password" />
      <div v-if="passWordError" class="error">{{ passWordError }}</div>
      <label>Role : </label>
      <select v-model="role">
        <option value="developer">Web Developer</option>
        <option value="designer">Web Designer</option>
      </select>
      <label>Skills:</label>
      <input type="text" v-model="tempSkill" @keyup.alt="addSkills" />
      <div
        v-for="(skill, index) in skills"
        :key="index"
        @click="deleteSkill(skill)"
        class="pill"
      >
        {{ skill }}
      </div>
      <div class="terms">
        <input type="checkbox" required v-model="terms" />
        <label>Accept terms and conditions</label>
      </div>
      <div class="submit">
        <button>Create an account</button>
      </div>
    </form>
    <p>Email : {{ email }}</p>
    <p>password : {{ password }}</p>
    <p>Role : {{ role }}</p>
    <p>Terms : {{ terms }}</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      terms: false,
      tempSkill: "",
      skills: [],
      passWordError: "",
    };
  },
  methods: {
    addSkills(e) {
      if (e.key === "," && this.tempSkill) {
        this.skills.push(this.tempSkill);
        this.skills = [...new Set(this.skills)];
        this.tempSkill = "";
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((item) => item !== skill);
    },
    handleSubmit() {
      this.passWordError =
        this.passWordError.length > 5
          ? ""
          : "password needs to be as least 6 letters";
    },
  },
};
</script>
<style scoped>
form {
  max-width: 420px;
  margin: 30px auto;
  background: #fff;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
p {
  text-align: center;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}
button {
  background: #0b6dff;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: #fff;
  border-radius: 20px;
}
.submit {
  text-align: center;
  cursor: pointer;
}
.submit button {
  cursor: pointer;
}
.error {
  color: #ff0062;
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
}
</style>
