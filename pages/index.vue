<template>
  <div class="container">
    <div class="row align-items-center">
      <div class="col-4">
        <Portrait />
      </div>
      <div class="col-md-8">
        <h1 class="title">Marc Sousbie</h1>
        <h2 class="subtitle">{{ $t('job') }}</h2>
        <p class="text-muted">{{ $t('message') }}</p>
      </div>
    </div>
    <div class="links">
      <nuxt-link
        v-for="locale in availableLocales"
        :key="locale.code"
        :to="switchLocalePath(locale.code)"
      >
        {{ locale.name }}
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    availableLocales() {
      return this.$i18n.locales.filter((i) => i.code !== this.$i18n.locale)
    },
  },
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 48px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
