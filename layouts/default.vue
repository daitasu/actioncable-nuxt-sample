<template>
  <div>
    <nav class="navbar header has-shadow is-primary" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <a class="navbar-item" href="/">
          <img src="~assets/buefy.png" alt="Buefy" height="28">
        </a>

        <div class="navbar-burger">
          <span/>
          <span/>
          <span/>
        </div>
      </div>
    </nav>

    <section class="main-content columns">
      <!-- <aside class="column is-2 section">
        <p class="menu-label is-hidden-touch">General</p>
        <ul class="menu-list">
          <li
            v-for="(item, key) of items"
            :key="key">
            <nuxt-link
              :to="item.to"
              exact-active-class="is-active">
              <b-icon :icon="item.icon"/> {{ item.title }}
            </nuxt-link>
          </li>
        </ul>
      </aside>-->
      <div class="container column is-12">
        <nuxt/>
      </div>
    </section>

    <nav class="navbar footer has-shadow is-primary" role="navigation" aria-label="main navigation">
      <b-field position="is-centered" class="column is-6" style="margin: auto">
        <b-input v-model="messageText" placeholder="メッセージ" class="message-box"/>
        <p class="control">
          <button class="button is-info" @click="handleClick">
            <span>送信</span>
          </button>
        </p>
      </b-field>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { title: "Home", icon: "home", to: { name: "index" } },
        { title: "Inspire", icon: "lightbulb", to: { name: "inspire" } }
      ],
      messageText: ""
    };
  },
  methods: {
    handleClick: function() {
      console.log(this.$store.state.messages);
      this.$store.commit("addMessage", this.messageText);
      this.messageText = ""
    }
  }
};
</script>

<style>
.footer {
  position: fixed;
  width: 100%;
  bottom: 0;
  padding: 2.5rem 1.5rem;
}
.message-box {
  width: 100%;
}
</style>