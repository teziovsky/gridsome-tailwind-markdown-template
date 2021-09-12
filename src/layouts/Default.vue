<template>
  <div>
    <Header />
    <transition appear name="fade">
      <main class="container mx-auto p-6 min-h-screen">
        <slot />
      </main>
    </transition>
    <Footer />
  </div>
</template>


<script>
import Header from '@/components/Header.vue';
import Footer from '@/components/Footer.vue';

export default {
  name: 'Default',
  components: {
    Header,
    Footer,
  },
};
</script>

<style>
body {
  font-family: Roboto, sans-serif;
}

.fade-enter-active {
  transition: opacity .5s;
}

.fade-enter {
  opacity: 0;
}
</style>
