<template>
  <v-app-bar
    v-scroll="onScroll"
    :color="!isScrolling ? 'transparent' : 'white'"
    fixed
    flat
  >
    <v-slide-x-transition>
      <v-img
        v-if="showLogo"
        :src="require('@/assets/logo.png')"
        class="shrink"
        contain
        height="50"
      />
    </v-slide-x-transition>

    <v-spacer />

    <social-media />

    <base-btn class="ml-3" large>
      <nuxt-link
        v-for="locale in availableLocales"
        :key="locale.code"
        class="langLink"
        :to="switchLocalePath(locale.code)"
      >
        {{ locale.name }}
      </nuxt-link>
    </base-btn>
  </v-app-bar>
</template>

<script>
export default {
  data: () => ({
    showLogo: false,
    isScrolling: false,
  }),

  computed: {
    availableLocales() {
      return this.$i18n.locales.filter((i) => i.code !== this.$i18n.locale)
    },
  },

  methods: {
    onScroll() {
      const offset = window.pageYOffset
      this.isScrolling = offset > 50
      this.showLogo = offset > 200
    },
  },
}
</script>

<style scoped>
.langLink {
  color: aliceblue;
}
</style>
