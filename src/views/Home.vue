<template>
  <div class="hero">
    <Header />
    <main class="home">
      Main
    </main>
    <Footer />
  </div>
</template>

<script>
// Components
import Header from '../components/layout/Header';
import Footer from '../components/layout/Footer';

export default {
  name: 'Home',
  components: {
    Header,
    Footer,
  },
};
</script>

<style scoped>
.hero {
  background: red;
}

.home {
  color: red;
}
</style>
