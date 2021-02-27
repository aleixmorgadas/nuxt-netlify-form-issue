<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        nuxt-netlify-form-issue
      </h1>
      <div class="links">
        <NuxtLink
          to="/contact"
          class="button--green"
        >
          Contact Form
        </NuxtLink>
        <a href="https://twitter.com/aleixmorgadas/status/1365693737515560964" class="button--grey" target="__blank">Thread of the report of the issue at Twitter</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
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
