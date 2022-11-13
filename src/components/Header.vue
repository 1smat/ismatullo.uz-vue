<script setup>
import routes from '../routes/routes.js'
import ScrollReveal from 'scrollreveal'
import { ref } from '@vue/reactivity'
import { onMounted } from '@vue/runtime-core'

const navToggle = ref(null)
const navMenu = ref(null)

onMounted(() => {
    function showMenu() {
        const toggle = navToggle.value
        const nav = navMenu.value

        if (toggle && nav) {
            toggle.addEventListener('click', () => {
                nav.classList.toggle('show')
                document.body.classList.toggle('stop-scrolling')
            })
        }
    }
    showMenu()

    const navLink = document.querySelectorAll('.nav__link')

    function linkAction() {
        const navMenu = document.getElementById('nav-menu')
        // When we click on each nav__link, we remove the show-menu class
        navMenu.classList.remove('show')
        document.body.classList.toggle('stop-scrolling')
    }
    navLink.forEach((n) => n.addEventListener('click', linkAction))

    /*==================== SCROLL SECTIONS ACTIVE LINK ====================*/
    const sections = document.querySelectorAll('section[id]')

    function scrollActive() {
        const scrollY = window.pageYOffset

        sections.forEach((current) => {
            const sectionHeight = current.offsetHeight
            const sectionTop = current.offsetTop - 50
            const sectionId = current.getAttribute('id')

            // console.log(current, "cureent")

            if (scrollY > sectionTop && scrollY <= sectionTop + sectionHeight) {
                document
                    .querySelector(`.nav__menu a[href*="${sectionId}"]`)
                    .classList.add('active')
            } else {
                document
                    .querySelector(`.nav__menu a[href*="${sectionId}"]`)
                    .classList.remove('active')
            }
        })
    }
    window.addEventListener('scroll', scrollActive)

    /*===== SCROLL REVEAL ANIMATION =====*/
    const sr = ScrollReveal({
        origin: 'top',
        distance: '60px',
        duration: 2000,
        delay: 200,
        //     reset: true
    })

    sr.reveal('.home__data, .about__img, .skills__subtitle, .skills__text', {})
    sr.reveal('.home__img, .about__subtitle, .about__text, .skills__img', {
        delay: 400,
    })
    sr.reveal('.home__social-icon', { interval: 200 })
    sr.reveal('.skills__data, .work__img, .contact__input', { interval: 200 })
})
</script>
<template>
    <header class="l-header">
        <nav class="nav bd-grid">
            <div>
                <a href="#" class="nav__logo" id="Home">Ismatullo</a>
            </div>

            <div class="nav__menu" id="nav-menu" ref="navMenu">
                <ul class="nav__list">
                    <li
                        class="nav__item"
                        v-for="route in routes"
                        :key="route.name"
                    >
                        <a
                            :href="route.scroll"
                            @click="setActive"
                            :class="
                                route.name === 'Home'
                                    ? 'nav__link active'
                                    : 'nav__link'
                            "
                        >
                            {{ route.name }}
                        </a>
                    </li>
                </ul>
            </div>

            <div class="nav__toggle" id="nav-toggle" ref="navToggle">
                <i class="bx bx-menu"></i>
            </div>
        </nav>
    </header>
</template>
