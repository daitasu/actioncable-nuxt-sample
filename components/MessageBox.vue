<template>
  <nav class="navbar footer has-shadow is-primary" role="navigation" aria-label="main navigation">
    <b-field position="is-centered" style="width: 100%">
      <b-input placeholder="メッセージ" class="message-box"/>
      <p class="control">
        <button class="button is-info">
          <span>送信</span>
          <b-icon icon="airplane"/>
        </button>
      </p>
    </b-field>
  </nav>
</template>

<style>
.footer {
  position: fixed;
  width: 100%;
  bottom:0;
  padding: 2.5rem 1.5rem;
}
.message-box {
  width: 40%;
}
</style>