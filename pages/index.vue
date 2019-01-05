<template>
  <section class="section">
    <div 
      v-for="(message, i) of messages" 
      :key="i" 
      class="columns message">
      <div class="card">
        <div>
          <div class="content has-text-lefted">
            <balloon :message="message"/>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Balloon from "@/components/Balloon";

export default {
  name: "HomePage",
  components: { Balloon},
  data() {
    return {
      messages: this.$store.state.messages
    };
  }
};
</script>

<style>
.message {
  width: 100%;
}
.card {
  width: 100%;
  padding: 0.5rem;
  box-shadow: none;
}
</style>