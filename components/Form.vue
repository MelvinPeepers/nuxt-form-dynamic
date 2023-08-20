<template>
    <div class="container">

        <h1>Netlify Forms on Nuxt 3</h1>

        <h2>Contact Form</h2>

        <p>Have any questions or suggestions?</p>

        <form 
            name="contact" 
            method="POST" 
            data-netlify="true"
            action="thank you"
            @submit.prevent="handleSubmit"
        >

            <input type="hidden" name="form-name" value="contact" />

            <div class="row">

                <div class="column">
                    <label>Name</label>
                    <input type="text" name="name" placeholder="Full name here">
                </div>

                <div class="column">
                    <label for="email">Email</label>
                    <input type="email" name="email" placeholder="Email">
                </div>

            </div>

            <div class="row">

                <div class="column">
                    <label>Title</label>
                    <input type="text" name="title" placeholder="Title of message">
                </div>

            </div>

            <div class="row">
                <div class="column">
                    <label>Message</label>
                    <textarea name="message" placeholder="Leave your message here"></textarea>
                </div>
            </div>

            <div class="vertical-center">
                <button type="submit">Submit</button>
            </div>

        </form>

    </div>

</template>

<style>
@import url("~/assets/styling.css");
</style>

<script setup>
import { onMounted, onUnmounted } from 'vue';

const handleSubmit = (event) => {
    event.preventDefault();
    const form = event.target;

    // Serialize form data
    const formData = new FormData(form);

    // Send the form data to Netlify
    fetch("/", {
        method: "POST",
        body: formData,
    })
        .then(() => {
            alert("Form submitted successfully!");
            // Handle any other success actions or redirects here
        })
        .catch((error) => {
            console.error("Error submitting the form:", error);
            // Handle error cases here
        });
};

onMounted(() => {
    // Attach the form submission event listener
    const form = document.querySelector("form[name='contact']");
    form.addEventListener("submit", handleSubmit);
});

onUnmounted(() => {
    // Remove the form submission event listener to avoid memory leaks
    const form = document.querySelector("form[name='contact']");
    form.removeEventListener("submit", handleSubmit);
});

// export default {
//     name: 'NuxtForm',
//     methods: {
//         handleSubmit(event) {
//             event.preventDefault();
//             const form = event.target;

//         // Serialize form data
//         const formData = new FormData(form);

//         // Send the form to Netlify
//         fetch("/", {
//             method: "POST",
//             body: FormData,
//         })
//             .then(() => {
//                 alert("Form submitted successfully!");
//                 // Handle any other success actions or redirects here
//             })
//             .catch((error) => {
//                 console.error("Error submitting the form:", error);
//                 // Handle error cases here
//             });
//         },
//     },
//     mounted() {
//         // Attach the form submission event listener
//         const form = document.querySelector("form[name='contact']");
//         form.removeEventListener(submit, this.handleSubmit);
//     }
// }
</script>