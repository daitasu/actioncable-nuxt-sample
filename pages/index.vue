<template>
  <section class="section">
    <!-- <div class="columns is-mobile"> -->
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
    <!-- <message-box /> -->
    <!-- </div> -->
  </section>
</template>

<script>
import Balloon from "@/components/Balloon";
import MessageBox from "@/components/MessageBox"

export default {
  name: "HomePage",
  components: { Balloon, MessageBox },
  data() {
    return {
      features: [
        {
          icon: "github-circle",
          title: "Free",
          content: `<span>Open source on <a href="https://github.com/buefy/buefy"> GitHub</a></span>`
        },
        {
          icon: "cellphone-link",
          title: "Responsive",
          content: `<span><b class="has-text-grey">Every</b> component is responsive</span>`
        },
        {
          icon: "alert-decagram",
          title: "Modern",
          content: `<span>Built with <a href="https://vuejs.org/">Vue.js</a> and <a href="http://bulma.io/">Bulma</a></span>`
        },
        {
          icon: "arrange-bring-to-front",
          title: "Lightweight",
          content: `<span>No other internal dependency</span>`
        }
      ],
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