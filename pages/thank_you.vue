<template>
  <div class="thankWrapper">
    <h1>
      Thank you for completing the test.<br />
      Our team will follow up for the next steps.
    </h1>
    <p>
      Enjoy the rest of the day!
    </p>
  </div>
</template>

<script>
import SignUp from "../components/form/SignUp.vue";
import SignUp1 from "../components/form/SignUp.vue";
import { mapMutations, mapState, mapGetters, mapActions } from "vuex";
export default {
  name: "ThankYouPage",
  head() {
    return {};
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
      "GET_EMAIL",
      "GET_TEST_ID"
    ])
  },
  methods: {}
};
</script>

<style scoped>
.thankWrapper {
  background-color: white;
  border-radius: 10px;
  display: block;
  margin: 0 auto;
  padding: 130px;
  margin-top: 15%;
}
.thankWrapper h1 {
  text-align: center;
}
.thankWrapper p {
  text-align: center;
}

@media only screen and (max-width: 600px) {
  .thankWrapper {
    padding: 40px;
  }
}
</style>
