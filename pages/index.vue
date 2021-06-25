<template>
  <div>
    <v-container
      style="
        padding-left: 10vw;
        padding-right: 10vw;
        padding-top: 5vw;
        padding-bottom: 5vw;
        background: url('~/assets/bg.png');
      "
    >
      <v-row align="center" justify="center">
        <v-col cols="5 ">
          <h1 class="display-3 section-title font-weight-black">FAST, FREE</h1>
          <h1 class="display-3 section-title font-weight-black">AND EASY.</h1>
          <p class="body-2 mt-2">
            If you scanned a QR Code today, chances are it was generated using
            QR Code Generator. We take mobile marketing to the next level and
            have helped thousands of companies achieve their business goals.
          </p>
          <v-row>
            <v-col>
              <v-btn color="primary">Get Started</v-btn>
              <v-btn color="primary" text>Get Started</v-btn>
            </v-col>
          </v-row>
        </v-col>

        <v-col cols="7">
          <v-img
            contain
            src="https://i.pinimg.com/originals/af/cc/7d/afcc7dd829be97c8e5eeb76ec40a86ff.png"
          ></v-img>
        </v-col>
      </v-row>
    </v-container>

    <div
      style="
        background: #1976d2;
        padding-top: 5vw;
        padding-bottom: 5vw;
        padding-left: 10vw;
        padding-right: 10vw;
      "
    >
      <qr-module />
    </div>
    <v-container
      style="
        padding-left: 10vw;
        padding-right: 10vw;
        padding-top: 5vw;
        padding-bottom: 5vw;
      "
    >
      <v-row align="center" justify="center">
        <v-col cols="6">
          <h1 class="display-3 section-title font-weight-bold">About us</h1>
          <p>
            Egoditor was founded in 2009 by Nils Drescher and Nils Engelking.
            They both saw the true potential of QR Codes when it was still under
            the radar. But when the impact on mobile marketing became obvious,
            QR-Code-Generator.com was already miles ahead.
          </p>
        </v-col>

        <v-col cols="6">
          <v-img
            src="https://www.qr-code-generator.com/wp-content/themes/qr/new_structure/assets/media/images/about_page/illustrations/about-us_illustration.png"
          ></v-img>
        </v-col>
      </v-row>

      <v-row align="center" justify="center">
        <v-col cols="6">
          <v-img
            contain
            src="https://www.qr-code-generator.com/wp-content/themes/qr/new_structure/assets/media/images/about_page/illustrations/socia-media_illustration.png"
          ></v-img>
        </v-col>

        <v-col cols="6">
          <h1 class="display-3 section-title font-weight-bold">
            Nice to meet you!
          </h1>
          <p class="mt-2 body-2">
            I'm <strong>Adrian Van Ladrillano </strong>
            Lorem ipsum dolor sit amet consectetur, adipisicing elit.
            Repudiandae aliquam necessitatibus doloribus quaerat, suscipit
            fugiat quod libero ut blanditiis nisi beatae! Minima commodi tenetur
            cumque harum inventore odit debitis minus.
          </p>

          <v-btn icon class="mr-5">
            <v-icon x-large>mdi-github</v-icon>
          </v-btn>

          <v-btn icon class="mr-5">
            <v-icon x-large>mdi-linkedin</v-icon>
          </v-btn>

          <v-btn icon class="mr-5">
            <v-icon x-large>mdi-facebook</v-icon>
          </v-btn>

          <v-btn icon class="mr-5">
            <v-icon x-large>mdi-twitter</v-icon>
          </v-btn>

          <v-btn icon class="mr-5">
            <v-icon x-large>mdi-instagram</v-icon>
          </v-btn>
        </v-col>
      </v-row>
    </v-container>

    <div
      class="py-10"
      style="background-color: #1976d2; padding-top: 5vw; padding-bottom: 5vw"
    >
      <v-row class="white--text">
        <v-col>
          <v-row align="center" justify="center">
            <v-card class="pt-5" width="800">
              <h1 class="display-2 section-title font-weight-bold text-center">
                Frequently Asked Questions.
              </h1>
              <p class="text-center">
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
              </p>
              <v-expansion-panels flat accordion class="mt-5">
                <v-expansion-panel v-for="(item, i) in faq" :key="i">
                  <v-expansion-panel-header>{{
                    item.title
                  }}</v-expansion-panel-header>
                  <v-expansion-panel-content>
                    {{ item.description }}
                  </v-expansion-panel-content>
                </v-expansion-panel>
              </v-expansion-panels>
            </v-card>
          </v-row>
        </v-col>
      </v-row>
    </div>
  </div>
</template>

<script>
import QrcodeVue from 'qrcode.vue'

export default {
  data() {
    return {
      value: 'https://example.com',
      size: 300,
      faq: [
        {
          title: 'Are you collecting my data?',
          description: "No, I don't need it."
        },
        {
          title: 'Why did you create this application?',
          description:
            "Many friends and relatives are asking me to create qr code for their stuff and i'm just sick of it. So to my future friends this is the answer."
        },
        {
          title: "Why it's free?",
          description:
            'This is just a sample projet for my portfolio and I just want to help people in their everyday needs.'
        },
        {
          title: 'Can I create a barcode?',
          description: 'Nope, please look at the title of the website.'
        },
        {
          title: 'Will you update this website for future features?',
          description: 'Ohhh yes'
        },
        {
          title: 'Do you hack?',
          description: 'No.'
        },
        {
          title: 'Can you create my website for free?',
          description: 'No. Just wait for my future applications'
        },
        {
          title: 'Are you selling my data to big companies?',
          description: "For the second time i'm not getting any data from you."
        }
      ]
    }
  }
}
</script>
<style>
.section-title {
  color: #1b294b;
}
</style>