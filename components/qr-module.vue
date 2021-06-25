<template>
  <div>
    <v-container>
      <!-- QR Selection -->
      <v-row class="text-center">
        <v-col>
          <h1 class="display-2 white--text font-weight-black">
            What type of QR Codes can I create for free?
          </h1>
          <p class="font-weight-black text-h4 mt-2">
            Forever free. Even the creator die.
          </p>
          <p class="mt-2 white--text">
            We offer these Static QR Codes that are completely for free and will
            never expire. Once generated, it’s yours forever but you will not be
            able to edit the content or track its scans.
          </p>
        </v-col>
      </v-row>
      <div v-if="qr_mode != null">
        <v-container fill-height height="100vh">
          <v-row>
            <v-col>
              <v-card height="100%" class="px-5 py-5">
                <v-btn @click="qr_mode = null">Back</v-btn>
                <v-textarea
                  v-if="qr_mode == 'URL'"
                  height="100%"
                  class="custom-label-color"
                  flat
                  solo
                  placeholder="Enter url here."
                  v-model="qr_url"
                ></v-textarea>

                <v-textarea
                  v-if="qr_mode == 'TEXT'"
                  height="100%"
                  class="custom-label-color"
                  flat
                  solo
                  placeholder="Enter text here."
                  v-model="qr_text"
                ></v-textarea>

                <!-- SMS -->
                <div v-if="qr_mode == 'SMS'">
                  <v-text-field
                    label="Your number"
                    outlined
                    dense
                    v-model="sms_number"
                  ></v-text-field>
                  <v-textarea
                    label="Message"
                    outlined
                    dense
                    v-model="sms_message"
                  ></v-textarea>
                </div>

                <!-- EMAIL -->
                <div v-if="qr_mode == 'EMAIL'">
                  <v-text-field
                    label="Your email"
                    outlined
                    dense
                    v-model="email_address"
                  ></v-text-field>
                  <v-text-field
                    label="Subject"
                    outlined
                    dense
                    v-model="email_subject"
                  ></v-text-field>
                  <v-textarea
                    label="Message"
                    outlined
                    dense
                    v-model="email_message"
                  ></v-textarea>
                </div>

                <!-- WIFI -->
                <div v-if="qr_mode == 'WIFI'">
                  <v-text-field
                    label="Network name"
                    outlined
                    dense
                    v-model="wifi_name"
                  ></v-text-field>
                  <v-text-field
                    label="Password"
                    outlined
                    dense
                    v-model="wifi_password"
                  ></v-text-field>
                  <v-autocomplete
                    label="Encryption"
                    :items="['None', 'WPA/WPA2', 'WEP']"
                    outlined
                    dense
                    v-model="wifi_enc"
                  ></v-autocomplete>
                </div>
              </v-card>
            </v-col>

            <v-col cols="4">
              <v-card class="px-5 py-5">
                <v-row>
                  <v-col class="px-10 py-5">
                    <qrcode-vue
                      :value="qr_value"
                      level="H"
                      :background="qr_bg"
                      :foreground="qr_fg"
                      size="300"
                    />
                  </v-col>
                </v-row>

                <v-row>
                  <v-col>
                    <v-text-field
                      v-model="qr_bg"
                      v-mask="mask"
                      hide-details
                      class="ma-0 pa-0"
                      solo
                    >
                      <template v-slot:append>
                        <v-menu
                          v-model="menu"
                          top
                          nudge-bottom="105"
                          nudge-left="16"
                          :close-on-content-click="false"
                        >
                          <template v-slot:activator="{ on }">
                            <div :style="swatchStyle" v-on="on" />
                          </template>
                          <v-card>
                            <v-card-text class="pa-0">
                              <v-color-picker v-model="qr_bg" flat />
                            </v-card-text>
                          </v-card>
                        </v-menu>
                      </template>
                    </v-text-field>
                  </v-col>
                </v-row>
                <v-row>
                  <v-col>
                    <v-text-field
                      v-model="qr_fg"
                      v-mask="mask2"
                      hide-details
                      class="ma-0 pa-0"
                      solo
                    >
                      <template v-slot:append>
                        <v-menu
                          v-model="menu2"
                          top
                          nudge-bottom="105"
                          nudge-left="16"
                          :close-on-content-click="false"
                        >
                          <template v-slot:activator="{ on }">
                            <div :style="swatchStyle2" v-on="on" />
                          </template>
                          <v-card>
                            <v-card-text class="pa-0">
                              <v-color-picker v-model="qr_fg" flat />
                            </v-card-text>
                          </v-card>
                        </v-menu>
                      </template>
                    </v-text-field>
                  </v-col>
                </v-row>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </div>

      <div v-if="qr_mode == null">
        <v-row>
          <v-col cols="4">
            <v-card @click="SelectQR('URL')">
              <v-card-title>URL</v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed
                accusamus deleniti porro exercitationem in. Laborum nemo unde
                beatae libero, porro voluptates nihil inventore fugit cum
                corporis! Voluptatum eligendi sed sunt.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="4">
            <v-card @click="SelectQR('TEXT')">
              <v-card-title>Plain Text</v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed
                accusamus deleniti porro exercitationem in. Laborum nemo unde
                beatae libero, porro voluptates nihil inventore fugit cum
                corporis! Voluptatum eligendi sed sunt.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="4">
            <v-card>
              <v-card-title>vCard</v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed
                accusamus deleniti porro exercitationem in. Laborum nemo unde
                beatae libero, porro voluptates nihil inventore fugit cum
                corporis! Voluptatum eligendi sed sunt.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="4">
            <v-card @click="SelectQR('SMS')">
              <v-card-title>SMS</v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed
                accusamus deleniti porro exercitationem in. Laborum nemo unde
                beatae libero, porro voluptates nihil inventore fugit cum
                corporis! Voluptatum eligendi sed sunt.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="4">
            <v-card @click="SelectQR('EMAIL')">
              <v-card-title>Email</v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed
                accusamus deleniti porro exercitationem in. Laborum nemo unde
                beatae libero, porro voluptates nihil inventore fugit cum
                corporis! Voluptatum eligendi sed sunt.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="4">
            <v-card @click="SelectQR('WIFI')">
              <v-card-title>Wifi</v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed
                accusamus deleniti porro exercitationem in. Laborum nemo unde
                beatae libero, porro voluptates nihil inventore fugit cum
                corporis! Voluptatum eligendi sed sunt.
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </div>
    </v-container>
  </div>
</template>
<script>
import QrcodeVue from 'qrcode.vue'

export default {
  components: {
    QrcodeVue
  },
  data() {
    return {
      // Colors
      qr_bg: '#FFFFFF',
      qr_fg: '#000000',

      //   types
      qr_url: '',
      qr_text: '',

      sms_number: '',
      sms_message: '',

      email_address: '',
      email_subject: '',
      email_message: '',

      wifi_name: '',
      wifi_password: '',
      wifi_enc: '',

      color: '#1976D2FF',
      mask: '!#000000',
      mask2: '!#FFFFFF',
      menu: false,
      menu2: false,

      qr_mode: null,
      value: 'https://example.com'
    }
  },
  computed: {
    qr_value() {
      if (this.qr_mode == 'URL') {
        return this.qr_url
      }
      if (this.qr_mode == 'TEXT') {
        return this.qr_text
      }
      if (this.qr_mode == 'SMS') {
        return 'smsto:' + this.sms_number + '?body=' + this.sms_message
      }
      if (this.qr_mode == 'EMAIL') {
        return (
          'mailto:' +
          this.email_address +
          '?subject=' +
          this.email_subject +
          '&body=' +
          this.email_message
        )
      }
      if (this.qr_mode == 'WIFI') {
        return `WIFI:T:WPA;S:${this.wifi_name};P:${this.wifi_password};H:`
      }
    },
    swatchStyle() {
      return {
        backgroundColor: this.qr_bg,
        cursor: 'pointer',
        height: '30px',
        width: '30px',
        border: '1px solid #e1e1e1',
        borderRadius: this.menu ? '50%' : '4px',
        transition: 'border-radius 200ms ease-in-out'
      }
    },
    swatchStyle2() {
      return {
        backgroundColor: this.qr_fg,
        cursor: 'pointer',
        height: '30px',
        width: '30px',
        border: '1px solid #e1e1e1',
        borderRadius: this.menu2 ? '50%' : '4px',
        transition: 'border-radius 200ms ease-in-out'
      }
    }
  },
  methods: {
    SelectQR(type) {
      this.qr_mode = type
    }
  }
}
</script>
<style>
.custom-placeholer-color textarea,
.custom-label-color textarea {
  font-size: 2em;
  font-weight: 700;
}
</style>