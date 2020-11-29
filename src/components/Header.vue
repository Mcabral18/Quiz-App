<template>
  <div>
    <b-nav tabs>
      <b-nav-item disabled>Quiz App</b-nav-item>
      <b-nav-item disabled>Questions: {{ questions.length }} </b-nav-item>
    </b-nav>
  </div>
</template>

<script>
export default {
  props: ["questions"],
};
</script>

<style>
</style>