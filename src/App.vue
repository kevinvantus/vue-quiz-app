<template>
  <main class="main-ctr">
    <h1 class="is-size-5 has-text-weight-medium">Vue Quiz App</h1>
    <callout></callout>
    <questions
      :questions="questions"
      :currentQuestion="currentQuestion"
    ></questions>
  </main>
</template>

<script>
import Callout from "@/components/Callout.vue";
import Questions from "@/components/Questions.vue";

export default {
  components: {
    Callout,
    Questions,
  },
  data() {
    return {
      currentQuestion: 0,
      questions: [
        {
          question: "What is the capital of France?",
          answers: ["Berlin", "Rome", "Paris", "Madrid"],
          correctAnswer: 2,
        },
        {
          question: "Which planet is known as the Red Planet?",
          answers: ["Mars", "Venus", "Jupiter", "Saturn"],
          correctAnswer: 0,
        },
        {
          question: "What is the largest mammal?",
          answers: ["Elephant", "Blue Whale", "Giraffe", "Hippopotamus"],
          correctAnswer: 1,
        },
        {
          question: "Who painted the Mona Lisa?",
          answers: [
            "Vincent van Gogh",
            "Pablo Picasso",
            "Leonardo da Vinci",
            "Claude Monet",
          ],
          correctAnswer: 2,
        },
        {
          question: "What gas do plants use for photosynthesis?",
          answers: ["Oxygen", "Carbon Dioxide", "Hydrogen", "Nitrogen"],
          correctAnswer: 1,
        },
        {
          question:
            "Which famous scientist developed the theory of general relativity?",
          answers: [
            "Isaac Newton",
            "Albert Einstein",
            "Galileo Galilei",
            "Stephen Hawking",
          ],
          correctAnswer: 1,
        },
        {
          question: "What is the largest organ in the human body?",
          answers: ["Liver", "Brain", "Heart", "Skin"],
          correctAnswer: 3,
        },
        {
          question: "Which gas do plants release during photosynthesis?",
          answers: ["Oxygen", "Carbon Dioxide", "Methane", "Nitrogen"],
          correctAnswer: 0,
        },
        {
          question: "In which year did the Titanic sink?",
          answers: ["1902", "1912", "1922", "1932"],
          correctAnswer: 1,
        },
        {
          question: "Who wrote the play 'Romeo and Juliet'?",
          answers: [
            "William Shakespeare",
            "Charles Dickens",
            "Mark Twain",
            "Jane Austen",
          ],
          correctAnswer: 0,
        },
      ],
    };
  },
};
</script>

<style lang="css" scoped></style>
