<script>
import routes from '../routes/routes.js'
export default {
    data() {
        return {
            routes,
        }
    },
}
</script>
<template>
    <header class="l-header">
        <nav class="nav bd-grid">
            <div>
                <a href="#" class="nav__logo">Ismatullo</a>
            </div>

            <div class="nav__menu" id="nav-menu">
                <ul class="nav__list">
                    <li
                        class="nav__item"
                        v-for="route in routes"
                        :key="route.name"
                    >
                        <a :href="route.scroll" class="nav__link">
                            {{ route.name }}
                        </a>
                    </li>
                </ul>
            </div>

            <div class="nav__toggle" id="nav-toggle">
                <i class="bx bx-menu"></i>
            </div>
        </nav>
    </header>
</template>
