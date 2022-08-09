<template>
  <div class="form">
    <!-- <div class="title">Welcome</div>
  <div class="subtitle">Let's create your account!</div> -->
    <div class="input-container ic1">
      <label for="firstname" class="placeholder">Name:</label>
      <input
        id="firstname"
        v-model="name"
        class="input"
        type="text"
        placeholder="Name"
      />
    </div>
    <p class="form-error">{{ errors && errors.name ? errors.name : null }}</p>

    <div class="input-container ic2">
      <input
        v-model="surname"
        id="surname"
        class="input"
        type="text"
        placeholder="Surname"
      />
      <label for="surname" class="placeholder">Surname:</label>
    </div>
    <p class="form-error">
      {{ errors && errors.surname ? errors.surname : null }}
    </p>
    <div class="input-container ic2">
      <label for="email" class="placeholder">Email:</label>
      <input
        v-model="email"
        id="email"
        class="input"
        type="email"
        placeholder="Email"
      />
    </div>
    <p class="form-error">{{ errors && errors.email ? errors.email : null }}</p>

    <p class="term-conditions">
      We are committed to protecting and respecting your privacy. In order to
      provide you our recruitment services, we need to store and process your
      personal data. If you consent to us storing your personal data for this
      purpose, please tick the checkbox below. I agree to allow TA Partners to
      store and process my personal data. For more information on our privacy
      practices, please review our
      <a class="primary-link" href="https://www.tapartners.org/privacy-policy"
        >Privacy Policy.</a
      >
    </p>

    <div class="checkbox-container">
      <label for=""
        ><input
          v-model="termsConditions"
          class="terms-check"
          type="checkbox"
        />I agree to allow TA Partners to store and process my personal
        data.</label
      >
    </div>
    <p class="form-error">
      {{ errors && errors.termsConditions ? errors.termsConditions : null }}
    </p>
    <button type="text" @click="SubmitForm" class="submit">
      START THE TEST NOW
    </button>
    <!-- <h1>{{GET_FIRST_NAME}}</h1> -->
  </div>
</template>

<script>
import { mapMutations, mapState, mapGetters, mapActions } from "vuex";
export default {
  data() {
    return {
      name: "",
      surname: "",
      email: "",
      termsConditions: false,
      errors: {
        name: "",
        surname: "",
        termsConditions: false,
        email: ""
      }
    };
  },
  computed: {
    ...mapState(["test", "development", "form", "loading"]),
    ...mapGetters([
      "GET_CURRENT_QUESTIONS",
      "GET_PROGRESS",
      "NEXT_BUTTON_STATE",
      "BACK_BUTTON_STATE",
      "GET_NAME",
      "GET_SURNAME",
      "GET_EMAIL"
    ])
  },

  methods: {
    SubmitForm() {
      // clear all form
      this.errors.name = "";
      this.errors.surname = "";
      this.errors.email = "";
      this.errors.termsConditions = "";
      if (this.name === "") {
        console.log("Name is empty");
        this.errors.name = "Please enter your name";
      }
      if (this.surname === "") {
        this.errors.surname = "Please enter your surname";
      }
      if (this.email === "") {
        this.errors.email = "Please enter your email correctly";
      }
      if (this.email !== "") {
        /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,24}))$/.test(
          this.email
        )
          ? " "
          : (this.errors.email = "Email is not correct");
      }
      if (this.termsConditions === false) {
        this.errors.termsConditions = "Please accept terms & conditions";
      } else {
        this.SET_NAME(this.name);
        this.SET_SURNAME(this.surname);
        this.SET_EMAIL(this.email);
        $nuxt.$router.push("/test");
      }
      return;
    },

    ...mapMutations([
      "SET_INVENTORY",
      "SET_NAME",
      "SET_SURNAME",
      "SET_EMAIL",
      "SET_ANSWER",
      "NEXT_QUESTIONS",
      "PREVIOUS_QUESTIONS",
      "SET_ITEMS_PER_PAGE",
      "SKIP_QUESTIONS"
    ]),
    ...mapActions(["SUBMIT_TEST"])
  }
};
</script>
<style>
.form-error {
  color: red;
  text-align: left;
  font-size: 13px;
}

.theme--light.v-icon {
  color: rgb(59 136 178) !important;
}

.checkbox-container {
  text-align: left;
  margin-top: 10px;
  margin-bottom: 10px;
}

.checkbox-container label {
  font-size: 13px;
}

.form {
  background-color: white;
  border-radius: 20px;
  box-sizing: border-box;
  /* height: 500px; */
  padding: 20px;
  width: 100%;
  float: right;
}

.title {
  color: rgba(0, 0, 0, 0.87);
  font-family: sans-serif;
  font-size: 36px;
  font-weight: 600;
  margin-top: 30px;
}

.subtitle {
  color: rgba(0, 0, 0, 0.87);
  font-family: sans-serif;
  font-size: 16px;
  font-weight: 600;
  margin-top: 10px;
}

.input-container {
  height: 50px;
  position: relative;
  width: 100%;
}

.ic1 {
  margin-top: 40px;
}

.ic2 {
  margin-top: 40px;
}

.input {
  background-color: #efeded69;
  border-radius: 12px;
  border: 0;
  box-sizing: border-box;
  color: rgba(0, 0, 0, 0.87);
  font-size: 18px;
  height: 100%;
  outline: 0;
  padding: 4px 20px 0;
  width: 100%;
}

.cut {
  background-color: #15172b;
  border-radius: 10px;
  height: 20px;
  left: 20px;
  position: absolute;
  top: -20px;
  transform: translateY(0);
  transition: transform 200ms;
  width: 76px;
}

.cut-short {
  width: 50px;
}

/* .input:focus ~ .cut,
.input:not(:placeholder-shown) ~ .cut {
  transform: translateY(8px);
} */

.placeholder {
  color: rgb(59, 136, 178);
  font-family: sans-serif;
  left: 10px;
  line-height: 14px;
  pointer-events: none;
  position: absolute;
  transform-origin: 0 50%;
  transition: transform 200ms, color 200ms;
  top: -20px;

  font-weight: 700;
}

.submit {
  background-color: rgb(59, 136, 178);
  border-radius: 12px;
  border: 0;
  box-sizing: border-box;
  color: #eee;
  cursor: pointer;
  font-size: 18px;
  height: 50px;

  outline: 0;
  text-align: center;
  width: 100%;
}

.submit:active {
  background-color: #06b;
}

.term-conditions {
  font-size: 13px;
  text-align: left;
  margin-top: 15px;
}

.primary-link,
.primary-link:hover {
  color: rgb(59, 136, 178) !important;
  font-weight: 600;
}

.terms-check {
  margin-top: 3px;
}
</style>
