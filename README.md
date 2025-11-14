<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Materi Matematika Interaktif dengan Canva</title>
    <style>
      * {
        box-sizing: border-box;
      }
      body {
        font-family: "Poppins", Times New Roman;
        margin: 0;
        background: linear-gradient(135deg, #b7c4f8, #414bb9);
        color: #eaf6ff;
        min-height: 100vh;
      }
      header {
        text-align: center;
        padding: 30px 20px;
      }
      header h1 {
        font-size: 28px;
        margin-bottom: 10px;
      }
      header p {
        color: #ffffff;
      }
      .container {
        max-width: 1000px;
        margin: 0 auto;
        padding: 20px;
      }
      .card {
        background: #9efae1;
        border: 1px solid rgba(250, 156, 232, 0.05);
        border-radius: 14px;
        padding: 20px;
        margin-bottom: 20px;
        transition: transform 0.3s ease, box-shadow 0.3s ease;
      }
      .card:hover {
        transform: translateY(-6px);
        box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
      }
      .card h2 {
        margin-top: 0;
        color: #ffffff;
      }
      .card p {
        color: #ffffff;
      }
      .link-btn {
        display: inline-block;
        background: #9efae1;
        color: rgb(255, 255, 255);;
        padding: 10px 18px;
        border-radius: 8px;
        text-decoration: none;
        transition: background 0.3s ease;
      }
      .link-btn:hover {
        background: #9efae1;
      }

      #quizPage {
        display: none;
      }
      #quizPage input[type="text"] {
        width: 80%;
        padding: 8px;
        border-radius: 6px;
        border: 1px solid #ccc;
        margin-right: 10px;
      }
      #quizPage button {
        padding: 8px 15px;
        border-radius: 6px;
        border: none;
        background: #9efae1;
        color: rgb(255, 255, 255);
        cursor: pointer;
      }
      #quizPage button:hover {
        background: #00d6e5;
      }

      footer {
        position: absolute;
        bottom: 20px;
        left: 0;
        width: 100%;
        text-align: center;
        color: #ffffff;
        padding: 30px 20px;
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Materi Pembelajaran Matematika Interaktif</h1>
      <p>
        Kumpulan materi matematika berbasis Canva yang menarik dan mudah
        dipahami untuk siswa.
      </p>
    </header>
    <main>
      <div id="homePage" class="container">
        <div class="card">
          <h2>1. Bilangan Berpangkat</h2>
          <p>
           Kumpulan materi matematika berbasis Canva yang menarik dan mudah dipahami untuk siswa.
          </p>
          <a
            href="https://www.canva.com/design/DAGzJRX0-uo/qGrYA0hsHAUGOy1Z_p2BuA/edit?utm_content=DAGzJRX0-uo&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton"
            target="_blank"
            class="link-btn"
            >Lihat di Canva</a
          >
        </div>
        <div class="card">
          <h2>2. Kuis Bilangan Berpangkat</h2>
          <p>Uji pemahamanmu dengan kuis berikut ini!</p>
          <a class="link-btn" onclick="startQuiz()">Mulai Kuis</a>
        </div>
      </div>

      <div id="quizPage" class="container">
        <a class="link-btn" onclick="showHome()">⬅ Kembali ke Beranda</a>
        <div class="card">
          <p id="quizQuestion"></p>
          <input
            type="text"
            id="quizInput"
            placeholder="Tulis jawabanmu di sini"
          />
          <button id="answerBtn" onclick="checkAnswer()">Jawab</button>
          <button id="nextBtn" onclick="nextQuestion()" style="display: none">
            Next
          </button>
          <p id="quizAnswer"></p>
        </div>
      </div>
    </main>
    <footer>
      © 2025 — Materi Interaktif Matematika | Dibuat oleh - Suci Putri
      Utami (B2B023030)
    </footer>
    <script>
      const quizData = [
        { question: "1. Jari-jari Lingkaran dilambangkan oleh?", answer: "r" },
        { question: "2. Apa hubungan diameter dan jari-jari?", answer: "Diameter = 2 × jari-jari." },
        { question: "3. Rumus keliling lingkaran apa?", answer: "K = 2 × π × r atau K = π × d." },
        { question: "4. Rumus Luas lingkaran?", answer: "L = π × r²." },
        { question: "5. Jika jari-jari lingkaran 7 cm, berapa diameternya?", answer: "Diameter = 2 × 7 = 14 cm."},
      ];

      let currentQuestion = 0;
      let score = 0;

      function startQuiz() {
        document.getElementById("homePage").style.display = "none";
        document.getElementById("quizPage").style.display = "block";
        currentQuestion = 0;
        score = 0;
        document.getElementById("quizInput").style.display = "inline-block";
        document.getElementById("answerBtn").style.display = "inline-block";
        showQuestion();
      }

      function showHome() {
        document.getElementById("quizPage").style.display = "none";
        document.getElementById("homePage").style.display = "block";
        document.getElementById("quizInput").style.display = "inline-block";
        document.getElementById("nextBtn").style.display = "none";
        document.getElementById("answerBtn").style.display = "inline-block";
      }

      function showQuestion() {
        document.getElementById("quizQuestion").textContent =
          quizData[currentQuestion].question;
        document.getElementById("quizInput").value = "";
        document.getElementById("quizAnswer").textContent = "";
        document.getElementById("nextBtn").style.display = "none";
        document.getElementById("answerBtn").style.display = "inline-block";
      }

      function checkAnswer() {
        const userAnswer = document.getElementById("quizInput").value.trim();
        if (userAnswer === "") {
          document.getElementById("quizAnswer").textContent =
            "⚠️ Isi jawaban terlebih dahulu!";
          return;
        }

        const correctAnswer = quizData[currentQuestion].answer;
        let feedback =
          userAnswer.toLowerCase() === correctAnswer.toLowerCase()
            ? "✅ Jawaban benar: " + correctAnswer
            : "❌ Jawaban salah. Jawaban yang benar: " + correctAnswer;

        if (userAnswer.toLowerCase() === correctAnswer.toLowerCase()) score++;

        document.getElementById("quizAnswer").textContent = feedback;
        document.getElementById("nextBtn").style.display = "inline-block";
        document.getElementById("answerBtn").style.display = "none";
      }

      function nextQuestion() {
        currentQuestion++;
        if (currentQuestion < quizData.length) {
          showQuestion();
        } else {
          document.getElementById("quizQuestion").textContent =
            "🎉 Kuis selesai!";
          document.getElementById("quizInput").style.display = "none";
          document.getElementById("answerBtn").style.display = "none";
          document.getElementById("nextBtn").style.display = "none";
          document.getElementById("quizAnswer").textContent =
            "Nilai akhir: " +
            score +
            " / " +
            quizData.length +
            ". Silakan kembali ke Beranda untuk mengulang kuis.";
        }
      }
    </script>
  </body>
</html>
