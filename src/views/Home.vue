<template>
  <div class="hero">
    <Header />
    <main class="home"></main>
    <Footer />
  </div>
</template>

<script>
// Components
import Header from '../components/layout/Header';
import Footer from '../components/layout/Footer';
import Button from '../components/ui/Button';

export default {
  name: 'Home',
  components: {
    Header,
    Footer,
    Button,
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
