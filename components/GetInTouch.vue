<template>
  <section id="get-in-touch" class="overflow-hidden">
    <v-row class="info white--text" no-gutters>
      <v-col class="pa-5" cols="12" md="6">
        <base-bubble-1 />

        <base-heading class="mb-5"> {{ $t('getintouch.title') }} </base-heading>

        <v-sheet color="transparent" max-width="600">
          <v-form
            v-model="valid"
            name="contact"
            method="post"
            data-netlify="true"
            data-netlify-honeypot="bot-field"
          >
            <input type="hidden" name="form-name" value="contact" />

            <v-text-field
              v-model="name"
              color="info"
              name="name"
              :label="$t('getintouch.name')"
              :placeholder="$t('getintouch.name')"
              solo
              flat
            />

            <v-text-field
              v-model="email"
              :rules="[rules.required, rules.email]"
              color="info"
              name="email"
              :label="$t('getintouch.email')"
              :placeholder="$t('getintouch.email')"
              solo
              flat
              required
            />

            <v-text-field
              color="info"
              name="subject"
              :label="$t('getintouch.subject')"
              :placeholder="$t('getintouch.subject')"
              solo
              flat
            />

            <v-textarea
              v-model="message"
              :rules="[rules.required]"
              color="info"
              name="message"
              :label="$t('getintouch.message')"
              :placeholder="$t('getintouch.message')"
              solo
              flat
              required
            />

            <base-btn type="submit" :disabled="!valid" @click="validate">{{
              $t('getintouch.send')
            }}</base-btn>
          </v-form>
        </v-sheet>
      </v-col>

      <v-col class="hidden-sm-and-down" md="6">
        <v-img :src="require('@/assets/contact.png')" height="100%" />
      </v-col>
    </v-row>
  </section>
</template>

<script>
export default {
  data() {
    return {
      valid: true,
      name: '',
      email: '',
      message: '',
      rules: {
        required: (value) => !!value || this.$i18n.t('getintouch.required'),
        email: (value) => {
          const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
          return pattern.test(value) || this.$i18n.t('getintouch.invalid')
        },
      },
    }
  },

  methods: {
    validate() {
      this.$refs.form.validate()
    },
  },
}
</script>
