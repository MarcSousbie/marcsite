<template>
  <div>
    <v-btn
      v-for="(item, i) in items.slice(0, large ? items.length : 4)"
      :key="i"
      fab
      class="ma-2"
      color="info"
      :small="!large"
      :href="item.link"
    >
      <NuxtLink v-if="item.name == 'Email'" to="#get-in-touch">
        <v-icon dark v-text="item.icon" />
      </NuxtLink>
      <v-icon v-else dark v-text="item.icon" />
    </v-btn>
  </div>
</template>

<script>
export default {
  props: {
    large: {
      type: Boolean,
      default: false,
    },
  },

  data: () => ({
    items: [
      {
        name: 'Twitter',
        icon: 'mdi-twitter',
        link: 'https://twitter.com/MarcSousbie',
      },
      {
        name: 'Linkedin',
        icon: 'mdi-linkedin',
        link: 'https://www.linkedin.com/in/marc-sousbie-0b5a1943/',
      },
      {
        name: 'Facebook',
        icon: 'mdi-facebook',
        link: 'https://www.facebook.com/marc.sousbie',
      },
      {
        name: 'Email',
        icon: 'mdi-email',
      },
    ],
  }),
}
</script>
