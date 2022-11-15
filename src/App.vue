<template>
    <Header />
    <main class="l-main">
        <Hero />
        <About />
        <Skills />
        <Works />
        <Contact />
    </main>

    <Footer />
</template>

<script>
import Header from './components/Header.vue'
import About from './components/About.vue'
import Hero from './components/Hero.vue'
import Skills from './components/Skills.vue'
import Works from './components/Works.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'

export default {
    components: {
        Header,
        Hero,
        About,
        Skills,
        Works,
        Contact,
        Footer,
    },
}
</script>
