<template>
  <v-footer class="pl-10 pt-10">
    <v-row class="footer-container">
      <v-col sm="12" md="6" class="pl-0 pt-0">
        <v-row class="footer-wrapper pl-0">
          <v-col cols="12" class="footer-about">
            Talent Acquisition Partners Srl<br />
            Via Alessandro Filippa 14<br />
            10139, Turin, Italy<br />
          </v-col>
          <v-col cols="12" class="pt-0">
            <a
              href="https://www.facebook.com/Tapartnersturin/"
              aria-label="Gå til facebook"
            >
              <v-icon large>{{ mdiFacebook }}</v-icon>
            </a>

            <v-divider inset vertical class="mx-1" />

            <a href="mailto:big5@tapartners.org" aria-label="Gå til twitter">
              <v-icon large>{{ mdiEmail }}</v-icon>
            </a>

            <v-divider inset vertical class="mx-1" />

            <a
              href="https://www.linkedin.com/company/talent-acquisition-partners"
              aria-label="Gå til linkedIn"
            >
              <v-icon large>{{ mdiLinkedin }}</v-icon>
            </a>
          </v-col>
          <v-col class="footer-text" cols="12">
            © {{ new Date().getFullYear() }} — Talent Acquisition Partners Srl -
            all rights reserved
          </v-col>
        </v-row>
      </v-col>
      <v-col cols="auto">
        <!-- <h3 class="mb-2">
          Having questions about or problems with the site?
        </h3> -->
        Please read our privay policy
        <a>
          <a
            class="primary-link"
            href="https://www.tapartners.org/privacy-policy"
            >here</a
          > </a
        >.
      </v-col>
    </v-row>
  </v-footer>
</template>

<script>
import {
  mdiFacebook,
  mdiTwitter,
  mdiGithub,
  mdiLinkedin,
  mdiEmail
} from "@mdi/js";

export default {
  name: "Footer",
  data: () => ({
    mdiFacebook,
    mdiTwitter,
    mdiLinkedin,
    mdiGithub,
    mdiEmail
  }),
  methods: {
    logClick(choice) {
      console.log(choice);
      this.$amplitude.getInstance().logEvent(`goes to ${choice}`, {});
    }
  }
};
</script>

<style scoped>
.footer-container {
  width: 100%;
  padding: 12px;
  margin-right: auto;
  margin-left: auto;
  max-width: 1200px;
}
.footer-heading {
  font-family: "Passion One", cursive;
  font-size: 4rem;
  color: #4c4f5a;
  line-height: 3.5rem;
}
.footer-about {
  letter-spacing: 0.1em;
}
.footer-text {
  font-family: "Didact Gothic", sans-serif;
  color: #b3b3b3;
}
.footer-wrapper {
  max-width: 1200px;
  width: 100%;
  padding: 12px;
  margin-right: auto;
  margin-left: auto;
}
</style>
