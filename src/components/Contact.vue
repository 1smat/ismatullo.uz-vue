
<script setup>
import { ref } from 'vue'
import axios from 'axios'


const name = ref("")
const email = ref("")
const message = ref("")

const send = () => {
    const url = 'http://localhost:80/new'
    const data = {
        name: name.value,
        email: email.value,
        message: message.value
    }
    axios.post(url, data)

    name.value = ''
    email.value = ''
    message.value = ''

    setTimeout(() => {
        alert('forma yuborildi')
    }, 300)
}

</script>


<template>
    <section class="contact section" id="contact">
        <h2 class="section-title">Contact
        </h2>

        <div class="contact__container bd-grid">
            <form class="contact__form">
                <input v-model="name" type="text" placeholder="Name" class="contact__input" />
                <input v-model="email" type="mail" placeholder="Email" class="contact__input" />
                <textarea v-model="message" name="" id="" cols="0" rows="10" class="contact__input"></textarea>
                <input @click="send" type="button" value="Submit" class="contact__button button" />
            </form>
        </div>
    </section>
</template>
