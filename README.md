# yes-no
testisting
<!DOCTYPE html>
<html>
<head>
  <title>Yes or No Quiz</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #f2f2f2;
    }

    .container {
      background-color: white;
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      padding: 40px;
      text-align: center;
      width: 360px;
    }

    img {
      width: 220px;
      height: auto;
      border-radius: 10px;
      margin-bottom: 20px;
      display: block;
      margin-left: auto;
      margin-right: auto;
    }

    button {
      margin: 10px;
      padding: 10px 25px;
      font-size: 16px;
      cursor: pointer;
      border-radius: 8px;
      border: none;
      background-color: #007bff;
      color: white;
      transition: background-color 0.2s;
    }

    button:hover:not(:disabled) {
      background-color: #0056b3;
    }

    button:disabled {
      background-color: #ccc;
      cursor: not-allowed;
    }

    #result {
      font-weight: bold;
      color: darkblue;
    }

    ul {
      list-style-type: none;
      padding: 0;
      text-align: left;
      margin-top: 20px;
    }

    li {
      background-color: #e9f1ff;
      border-radius: 6px;
      padding: 8px 12px;
      margin-bottom: 6px;
    }
  </style>
</head>
<body>

  <div class="container">
    <img id="questionImage" src="" alt="Question image">
    <h2 id="questionText"></h2>
    <div>
      <button id="yesBtn" onclick="answer('Yes')">Yes</button>
      <button id="noBtn" onclick="answer('No')">No</button>
    </div>
    <button id="nextBtn" onclick="nextQuestion()" disabled>Next</button>
    <div id="result"></div>
  </div>

  <script>
    const questions = [
      { text: "Do you like coffee?", image: "coffee.gif" },
      { text: "Do you enjoy playing games?", image: "godzilla.gif" },
      { text: "Do you have a pet?", image: "pet.gif" },
      { text: "Do you like traveling?", image: "travel.gif" },
      { text: "Do you prefer summer over winter?", image: "summer.gif" }
    ];

    let current = 0;
    const answers = [];

    function loadQuestion() {
      document.getElementById("result").textContent = "";
      document.getElementById("nextBtn").disabled = true;

      const q = questions[current];
      document.getElementById("questionText").textContent = q.text;
      document.getElementById("questionImage").src = q.image;
    }

    function answer(choice) {
      answers[current] = choice;
      document.getElementById("nextBtn").disabled = false;
    }

    function nextQuestion() {
      current++;
      if (current < questions.length) {
        loadQuestion();
      } else {
        showResults();
      }
    }

    function showResults() {
      let summary = "<h2>Quiz Completed!</h2><p>Your answers:</p><ul>";
      for (let i = 0; i < questions.length; i++) {
        summary += `<li>Q${i+1}: ${questions[i].text} — <strong>${answers[i]}</strong></li>`;
      }
      summary += "</ul><p>Thank you for completing the quiz!</p>";

      document.querySelector(".container").innerHTML = summary;
    }

    loadQuestion();
  </script>

</body>
</html>
