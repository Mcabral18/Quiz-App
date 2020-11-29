<template>
  <div id="app">
    <Header :questions="questions" />
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <!-- v-if="questions.length" if the array is empty then the length will be 0 and
          the questions box wont render  -->
          <question-box
            v-if="questions.length"
            :questions="questions[index]"
            :next="next"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import QuestionBox from "./components/QuestionBox.vue";

export default {
  name: "App",
  data() {
    return {
      questions: [],
      index: 0,
    };
  },
  components: {
    Header,
    QuestionBox,
  },
  // mounted() {
  //   fetch("https://opentdb.com/api.php?amount=10&category=27&type=multiple")
  //     .then((response) => response.json())
  //     .then((data) => (this.questions = data.results));
  // },
  async mounted() {
    const response = await fetch(
      "https://opentdb.com/api.php?amount=10&category=27&type=multiple"
    );
    const data = await response.json();
    this.questions = data.results;
  },
  methods: {
    //method to increment index value to change question
    next() {
      this.index++;
    },
  },
};
</script>

<style>
</style>