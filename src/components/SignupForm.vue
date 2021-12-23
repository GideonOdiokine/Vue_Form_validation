<template>
  <form @submit="handleSubmit">
    <label> Email: </label>
    <input type="email" required v-model="email" />

    <label> Password: </label>
    <input type="password" v-model="password" required />
    <div v-if="passwordError" class="danger">
      <p>{{ passwordError }}</p>
    </div>

    <label>Role </label>
    <select v-model="role">
      <option value="developer">Web developer</option>
      <option value="designer">Web designer</option>
    </select>

    <labal>Skills: </labal>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>

    <div class="terms">
      <input type="checkbox" required v-model="isChecked" />
      <label> Accept terms and condition</label>
    </div>

    <div class="submit">
      <button>Create an account</button>
    </div>
  </form>

  <!-- <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms: {{ isChecked }}</p>
  <h6>Names: {{ names }}</h6> -->
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      isChecked: false,
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
    deleteSkill(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item;
      });
    },
    handleSubmit(e) {
      e.preventDefault();
      // Validate password
      this.passwordError =
        this.password.length > 5
          ? ""
          : "Password must be at least 6 character long";

      if (!this.passwordError) {
        console.log(`Email:  ${this.email}`);
        console.log(`Password:  ${this.password}`);
        console.log(`Terms:  ${this.isChecked}`);
        console.log(`Role:  ${this.role}`);
        console.log(`Skills:`, this.skills);
      }
    },
  },
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
.danger {
  color: red;
  margin-top: 10px;
  font-weight: bold;
  font-size: 0.8em;
}
label {
  color: #aaa;
  display: inline-block;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input {
  display: block;
  padding: 18px 6px;
  width: 100%;
  box-sizing: border-box;
  border-bottom: 1px solid #ddd;
  color: #555;
  border: none;
}
select {
  display: block;
  padding: 18px 6px;
  width: 100%;
  box-sizing: border-box;
  border-bottom: 1px solid #ddd;
  color: #555;
}
.terms {
  margin: 10px 0;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: inherit;
  top: 12px;
}
.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eee;
  border-radius: 20px;
  font-size: 12px;
  font-weight: bold;
  cursor: pointer;
  letter-spacing: 1px;
  color: #777;
}
button {
  background: #0b6dff;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
  cursor: pointer;
}
.submit {
  text-align: center;
}
</style>
