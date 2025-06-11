<template>
  <section id="main-contact" class="section-5">
    <div class="contact">
      <div class="form-container">
        <h2>Contact Me</h2>
        <form method="POST" action="https://formspree.io/f/xeqvkzbo">
          <div class="input-field">
            <input id="name" type="text" required />
            <label for="name">Name*</label>
          </div>
          <div class="input-field">
            <input id="email" type="email" required />
            <label for="email">Email*</label>
          </div>
          <div class="input-field">
            <textarea id="messages" rows="5" required></textarea>
            <label for="messages">Messages*</label>
          </div>
          <button type="submit" class="btn">Send</button>
        </form>
      </div>
    </div>
    <div class="quote">
      <h4>
        “Your most unhappy customers are your greatest source of learning.”
        <br /><br /><b>~ Bill Gates ~</b>
      </h4>
    </div>
  </section>
</template>