<template>

  <div class="heading">
    <h1>Textfield highlighing DEMO</h1>
  </div> <!-- /head -->

  <div class="container">
    <div class="backdrop">
      <div class="highlights" v-html="highlights" ></div>
    </div>
    <textarea
        class="highlightsInput"
        v-model="message"
        @input="highlighting"
    ></textarea>
  </div><!-- /container -->

  <div class="perspectiveSwitch">
    <button type="button" v-on:click="perspectiveSwitch">Perspective</button>
  </div><!-- /perspectiveSwitch -->

  <div class="reference">
    <a href="https://codersblock.com/blog/highlight-text-inside-a-textarea/" target=”_blank”>reference</a>
    <pre>
      Rewritten in vue.js without jquery
      This version prevents the use of HTML injections
      by replacing '&lt' and '&gt' with HTML specialchars
    </pre>
  </div><!-- /reference -->

</template>

<script>
export default {
  name: "App",
  mounted() {
    this.highlightInput = document.querySelector(".highlightsInput");
    this.highlightInput
        .addEventListener('scroll', this.scrollTextArea)

  },
  destroyed() {
    this.highlightInput
        .removeEventListener('scroll', this.scrollTextArea)
  },
  data() {
    return {
      highlightInput: '',
      message: '',
      highlights: '',
      highlightsTop: 0,
    }
  },
  methods: {
    highlighting: function () {
      this.highlights = this.message
        .replace(/\n$/g, '\n\n')
        .replace(/</g, '&lt')  // prevents HTML injections
        .replace(/>/g, '&gt')  //
        .replace(
            /[A-Z].*?\b/g,
            '<mark style="border-radius: 3px; color: transparent; background-color: #ec9f9e;">$&</mark>'
        )

    },
    scrollTextArea : function () {
      console.log("SCROOOOOOOOOL MORTY !");
      this.highlightsTop = this.highlightInput.scrollTop;
      console.log(this.highlightsTop);
      document.querySelector(".backdrop")
          .scrollTop = this.highlightsTop;

    },
    perspectiveSwitch : function () {
      console.log("I SAID SWITCH MORTY !");
      document.querySelector('.container')
        .classList.toggle('perspective');
    }
  }
}
</script>
<style scoped>
  @import 'test.css';
</style>
