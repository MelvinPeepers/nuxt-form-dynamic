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
  >

    <div class="row">

        <div class="column">
            <label for="name">Name</label>
            <input type="text" id="name" name="name" placeholder="Full name here">
        </div>

        <div class="column">
            <label for="email">Email</label>
            <input type="email" id="email" name="email" placeholder="Email">
        </div>

    </div>

    <div class="row">

        <div class="column">
            <label for="subject">Title</label>
            <input type="text" id="title" name="title" placeholder="Title of message">
        </div>

    </div>

    <div class="row">
        <div class="column">
            <label for="message">Message</label>
            <textarea id="message" name="message" placeholder="Leave your message here"></textarea>
        </div>
    </div>

    <button type="submit">Submit</button>

</form>

</div>

</template>

<style>
@import url("/components/styling.css")
</style>

<script>
export default {
  name: 'NuxtForm'
}
</script>