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
import ActionCable from 'actioncable';

export default {
  data() {
    return {
      messageText: ""
    };
  },
  created() {
    const websocketUrl = `ws://${process.env.BASE_URL}/cable`;
    const cable = ActionCable.createConsumer(websocketUrl);

    this.messageChannel = cable.subscriptions.create( "PostChannel",{
      received: (data) => {
        this.$store.commit("addMessage", data);
      },
    })
  },
  methods: {
    handleClick: function() {
      //ActionCable PostChannelにおけるpostメソッドを実行する
      this.messageChannel.perform('post', { 
        message: this.messageText, 
      });
      //メッセージ追加後にテキストボックスを空にする
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