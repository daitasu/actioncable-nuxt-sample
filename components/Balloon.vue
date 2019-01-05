<template>
  <div id="balloon" class="balloon">
    <b-icon icon="github-circle" size="is-large" type="is-primary"/>
    <div class="message-text">{{ message.text }}</div>
  </div>
</template>

<script>
export default {
  props: {
    message: {
      type: Object,
      default: function () {
        return { 
          username: 'guest',
          imageTag: '',
          text: ''
        }
      }
    }
  }
};
</script>

<style>
.balloon {
  display: flex;
  position: relative;
  align-items: center;
}
.message-text {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
  display: flex;
  align-items: center;
  margin-left: 60px;
  border-radius: 15px;
  padding: 10px;
  box-shadow: 0 2px 3px rgba(10, 10, 10, 0.1), 0 0 0 1px rgba(10, 10, 10, 0.1);
}
</style>
