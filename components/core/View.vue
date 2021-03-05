<template>
  <div>
    <welcome />

    <services />

    <about-me />

    <get-in-touch />
  </div>
</template>

<script>
export default {
  name: 'CoreView',

  components: {
    AboutMe: () => import('@/components/AboutMe'),
    GetInTouch: () => import('@/components/GetInTouch'),
    Services: () => import('@/components/Services'),
    Welcome: () => import('@/components/Welcome'),
  },
}
</script>
