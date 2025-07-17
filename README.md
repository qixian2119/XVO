const questions = [
  {
    text: "What is the synonym of 'happy'?",
    answers: ["Sad", "Angry", "Joyful", "Tired"],
    correctIndex: 2
  },
  {
    text: "Translate: 'Con mèo'",
    answers: ["Dog", "Cat", "Bird", "Mouse"],
    correctIndex: 1
  },
  {
    text: "Complete: 'She ___ to school every day.'",
    answers: ["go", "goes", "gone", "going"],
    correctIndex: 1
  }
];

let currentQuestion = 0;
let score = 0;

const questionEl = document.getElementById('question');
const answersEl = document.getElementById('answers');
const resultEl = document.getElementById('result');

function showQuestion() {
  const q = questions[currentQuestion];
  questionEl.textContent = q.text;
  answersEl.innerHTML = '';
  q.answers.forEach((ans, idx) => {
    const btn = document.createElement('div');
    btn.className = 'answer';
    btn.textContent = ans;
    btn.onclick = () => checkAnswer(idx);
    answersEl.appendChild(btn);
  });
}

function checkAnswer(index) {
  if (index === questions[currentQuestion].correctIndex) {
    score++;
  }
  currentQuestion++;
  if (currentQuestion < questions.length) {
    showQuestion();
  } else {
    showResult();
  }
}

function showResult() {
  game.innerHTML = '';
  resultEl.textContent = `You got ${score} out of ${questions.length} correct!`;
}

showQuestion();
