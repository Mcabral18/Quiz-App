<template>
  <div class="question-box-container">
    <div>
      <b-jumbotron>
        <template #lead>
          {{ questions.question }}
        </template>

        <hr class="my-4" />

        <b-list-group>
          <b-list-group-item
            v-for="(answer, index) in answers"
            :key="index"
            @click.prevent="selectAnswer(index)"
            v-bind:class="[selectedIndex === index ? 'selected' : ``]"
            >{{ answer }}</b-list-group-item
          >
        </b-list-group>

        <b-button @click.prevent="next" variant="primary" href="#"
          >Submit</b-button
        >
      </b-jumbotron>
    </div>
  </div>
</template>

<script>
// we will use shufle js library to shufle our answers
// to use shufle we will pass the computed mehtod to a watch method
// we need to import shuffle library from lodash
export default {
  props: ["questions", "next"],
  data() {
    return {
      selectedIndex: null,
    };
  },
  computed: {
    //   this computed function create an array callled answers and join to it the correct_anwers
    //   and the incorrect_answers
    answers() {
      let answers = [...this.questions.incorrect_answers];
      answers.push(this.questions.correct_answer);
      return answers;
    },
  },
  methods: {
    selectAnswer(index) {
      this.selectedIndex = index;
      console.log(this.selectedIndex);
    },
  },
};
</script>

<style>
.btn {
  margin: 1rem;
}

.list-group-item:hover {
  background: #eee;
  cursor: pointer;
}

.selected {
  background-color: lightblue;
}

.correct {
  background-color: green;
}

.incorrect {
  background-color: red;
}
</style>