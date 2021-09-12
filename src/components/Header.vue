<template>
  <header class="p-6 border-b border-gray-600 flex flex-col md:flex-row items-center justify-between text-center">
    <strong>
      <g-link class="text-2xl" to="/">{{ $static.metadata.siteName }}</g-link>
    </strong>
    <nav class="flex gap-x-8 text-gray-500">
      <g-link class="nav__link" to="/">Home</g-link>
      <g-link class="nav__link" to="/blog/">Blog</g-link>
    </nav>
  </header>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
export default {
  name: 'Header',
};
</script>

<style scoped>
.nav__link {
  @apply hover:text-green-800 focus:text-green-800
}

.active--exact { /* Active Nav Link */
  @apply text-gray-900;
}
</style>