<template>
  <div id="app" class="quiz-container">
    <div v-if="showQuiz" class="quiz-question">
      <h1>{{ currentQuestion.question }}</h1>
      <ul class="answer-options">
        <li v-for="(answer, index) in currentQuestion.answers" :key="index">
          <button @click="selectAnswer(answer)">
            {{ answer }}
          </button>
        </li>
      </ul>
    </div>
    <div v-else class="quiz-completed">
      <h2>Quiz completed! Your score: {{ score }}/{{ questions.length }}</h2>
      <button @click="resetQuiz">Retry</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showQuiz: true,
      currentQuestionIndex: 0,
      score: 0,
      questions: [
        {
          question: "Who is the 2023 president of the Philippines?",
          answers: ["President Arroyo", "President Marcus", "President Duterte", "President Robredo"],
          correctAnswer: "President Marcus"
        },
        {
          question: "What is the national fruit of the Philippines?",
          answers: ["Apple", "StarApple", "Mango", "Guava"],
          correctAnswer: "Mango"
        },
        {
          question: "What is the national flower of the Philippines?",
          answers: ["Sampaguita", "Rose", "Gumamela", "Santan"],
          correctAnswer: "Sampaguita"
        },
        {
          question: "What is the national tree of the Philippines?",
          answers: ["Mahugany", "Narra", "Coconut", "Jackfruit"],
          correctAnswer: "Narra"
        },
        {
          question: "CSS stands for?",
          answers: ["Code Style Sheets", "Command Sheets Style", "Cascading Style Sheets", "Cascading Sheets Style"],
          correctAnswer: "Cascading Style Sheets"
        },
        {
          question: "What does HTML stand for?",
          answers: ["Hypertext Markup Language", "Hyperlink and Text Markup Language", "Home Tool Markup Language", "Hyper Transfer Markup Language"],
          correctAnswer: "Hypertext Markup Language"
        },
        {
          question: "What does EDM stand for?",
          answers: ["Enterprise Database Management", "Electronic Dance Music", "Emergency Disaster Management", " Electronic Direct Mail"],
          correctAnswer: "Enterprise Database Management"
        },
        {
          question: "What does BSIT stand for?",
          answers: ["Bachelor of System Information Technology", "Bachelor of Science in Information Technology", "Bachelor of System in Information Technology ", "Bachelor of Science in Industrial Technology"],
          correctAnswer: "Bachelor of Science in Information Technology"
        },
        {
          question: "Who is the 2023 Vice-President of the Philippines?",
          answers: ["V-President Paolo Duterte", "V-President Sara Duterte", "V-President Robredo", "V-President Marcus"],
          correctAnswer: "V-President Sara Duterte"
        },
        {
          question: "Who is our Platform Technologies 2 teacher?",
          answers: ["Sir Nicasio Amoin", "Sir Jonus Berdon", "Sir Mat Mitcheil Ando", "Sir Jeffrey Alerta"],
          correctAnswer: "Sir Mat Mitcheil Ando"
        }
      ]
    };
  },
  computed: {
    currentQuestion() {
      return this.questions[this.currentQuestionIndex];
    }
  },
  methods: {
    selectAnswer(answer) {
      if (answer === this.currentQuestion.correctAnswer) {
        this.score++;
      }

      if (this.currentQuestionIndex < this.questions.length - 1) {
        // Move to the next question
        this.currentQuestionIndex++;
      } else {
        // Quiz completed
        this.showQuiz = false;
      }
    },
    resetQuiz() {
      this.showQuiz = true;
      this.currentQuestionIndex = 0;
      this.score = 0;
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
}

.quiz-container {
  max-width: 600px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: purple;
}

.quiz-question h1 {
  margin-bottom: 20px;
}

.answer-options {
  list-style-type: none;
  padding: 0;
}

.answer-options li {
  margin: 10px 0;
}

button {
  padding: 10px;
  cursor: pointer;
}

button:hover {
  background-color: #ddd;
}

.quiz-completed {
  margin-top: 40px;
}

.quiz-completed h2 {
  margin-bottom: 20px;
}
</style>
