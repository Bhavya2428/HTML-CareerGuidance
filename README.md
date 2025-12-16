# HTML-CareerGuidance
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Career Guidance & Skill Development</title>

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:'Segoe UI',sans-serif;
}
body{
  background:linear-gradient(135deg,#c3ecff,#fdfbfb);
}
header{
  padding:20px 40px;
  background:rgba(255,255,255,0.85);
  display:flex;
  justify-content:space-between;
  align-items:center;
}
header h1{color:#4a6cf7;}
nav a{
  margin-left:20px;
  text-decoration:none;
  color:#555;
  font-weight:500;
  cursor:pointer;
}
section{
  display:none;
  padding:60px;
}
button{
  padding:12px 30px;
  border:none;
  border-radius:25px;
  background:#4a6cf7;
  color:white;
  cursor:pointer;
}

/* HOME */
#home{
  display:block;
  text-align:center;
}
#home h2{font-size:40px;margin-bottom:15px;}
#home p{font-size:18px;color:#555;}

/* LOGIN */
.login-box{
  max-width:350px;
  margin:0 auto;
  background:white;
  padding:30px;
  border-radius:20px;
  box-shadow:0 10px 25px rgba(0,0,0,0.1);
  text-align:center;
}
.login-box input{
  width:100%;
  padding:10px;
  margin:10px 0;
}

/* CAREERS */
.career-container{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:25px;
}
.card{
  background:white;
  padding:30px;
  border-radius:20px;
  box-shadow:0 10px 25px rgba(0,0,0,0.1);
}
.card h3{color:#4a6cf7;margin-bottom:10px;}
.step{
  background:#eef3ff;
  padding:10px;
  border-left:5px solid #4a6cf7;
  margin-bottom:10px;
  border-radius:8px;
}

/* QUIZ */
.quiz-box{
  max-width:500px;
  margin:0 auto;
  background:white;
  padding:30px;
  border-radius:20px;
  box-shadow:0 10px 25px rgba(0,0,0,0.1);
}
.quiz-box h3{margin-bottom:20px;}
.quiz-box label{
  display:block;
  margin-bottom:10px;
}
.result{
  margin-top:20px;
  font-size:18px;
  font-weight:bold;
  text-align:center;
  color:#2d2e32;
}

footer{
  text-align:center;
  padding:20px;
  background:rgba(255,255,255,0.7);
  margin-top:40px;
}
</style>
</head>

<body>

<header>
  <h1>Career Guidance</h1>
  <nav>
    <a onclick="showPage('home')">Home</a>
    <a onclick="showPage('login')">Login</a>
    <a onclick="showPage('career')">Careers</a>
    <a onclick="showPage('quiz')">Quiz</a>
  </nav>
</header>

<!-- HOME -->
<section id="home">
  <h2>Career Guidance & Skill Development</h2>
  <p>Helping students choose the right career path</p>
  <br>
  <button onclick="showPage('login')">Get Started</button>
</section>

<!-- LOGIN -->
<section id="login">
  <div class="login-box">
    <h2>Student Login</h2>
    <input type="text" placeholder="Username">
    <input type="password" placeholder="Password">
    <button onclick="showPage('career')">Login</button>
  </div>
</section>

<!-- CAREERS -->
<section id="career">
  <h2 style="text-align:center;">Explore Career Paths</h2><br>

  <div class="career-container">
    <div class="card">
      <h3>Information Technology (IT)</h3>
      <p>For students interested in computers & coding.</p>
      <div class="step">Programming Basics</div>
      <div class="step">DSA & Problem Solving</div>
      <div class="step">Web / App Development</div>
      <div class="step">Projects & Internships</div>
    </div>

    <div class="card">
      <h3>Medical</h3>
      <p>For students passionate about healthcare.</p>
      <div class="step">PCB in 12th</div>
      <div class="step">NEET Preparation</div>
      <div class="step">MBBS / Nursing</div>
      <div class="step">Hospital Practice</div>
    </div>

    <div class="card">
      <h3>Civil Services</h3>
      <p>For leadership & public service aspirants.</p>
      <div class="step">Graduation</div>
      <div class="step">UPSC Preparation</div>
      <div class="step">Prelims & Mains</div>
      <div class="step">Interview & Training</div>
    </div>
  </div>
</section>

<!-- QUIZ -->
<section id="quiz">
  <h2 style="text-align:center;">Career Aptitude Quiz</h2><br>

  <div class="quiz-box">
    <h3>1. What do you enjoy most?</h3>
    <label><input type="radio" name="q1" value="it"> Working with technology</label>
    <label><input type="radio" name="q1" value="medical"> Helping sick people</label>
    <label><input type="radio" name="q1" value="civil"> Managing people & society</label>

    <h3>2. Your strongest skill?</h3>
    <label><input type="radio" name="q2" value="it"> Logical thinking</label>
    <label><input type="radio" name="q2" value="medical"> Empathy & care</label>
    <label><input type="radio" name="q2" value="civil"> Leadership</label>

    <h3>3. Preferred work style?</h3>
    <label><input type="radio" name="q3" value="it"> Desk / Computer work</label>
    <label><input type="radio" name="q3" value="medical"> Hospital / Field work</label>
    <label><input type="radio" name="q3" value="civil"> Administrative work</label>

    <br>
    <button onclick="calculateResult()">Submit Quiz</button>
    <div class="result" id="quizResult"></div>
  </div>
</section>

<footer>
  Impact: Guiding youth toward meaningful careers 🌱
</footer>

<script>
function showPage(page){
  document.querySelectorAll("section").forEach(sec=>sec.style.display="none");
  document.getElementById(page).style.display="block";
}

function calculateResult(){
  let score = {it:0, medical:0, civil:0};

  ["q1","q2","q3"].forEach(q=>{
    let ans = document.querySelector(`input[name="${q}"]:checked`);
    if(ans) score[ans.value]++;
  });

  let best = Object.keys(score).reduce((a,b)=>score[a]>score[b]?a:b);

  let resultText = "";
  if(best==="it") resultText = "💻 You are best suited for a career in Information Technology.";
  if(best==="medical") resultText = "🩺 You are best suited for a career in Medical field.";
  if(best==="civil") resultText = "🏛 You are best suited for Civil Services.";

  document.getElementById("quizResult").innerText = resultText;
}
</script>

</body>
</html>
