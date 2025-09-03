# Future-vision
This is my first git hub repository 
Author= Akashdeep chauhan 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AI Career & Skills Advisor Tool</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #6a11cb, #2575fc);
      margin: 0; 
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }

    .container {
      background: white;
      padding: 40px;
      border-radius: 20px;
      box-shadow: 0 15px 30px rgba(0,0,0,0.25);
      text-align: center;
      max-width: 900px;
      width: 90%;
    }

    header {
      font-size: 30px;
      font-weight: bold;
      color: #2575fc;
      margin-bottom: 25px;
    }

    h2 { color: #333; margin-bottom: 15px; }
    p { color: #555; line-height: 1.6; }
    
    .career-options {
      display: flex;
      justify-content: center;
      gap: 30px;
      flex-wrap: wrap;
      margin: 20px 0;
    }

    .career-options input[type="radio"] {
      transform: scale(1.3);
      margin-right: 8px;
    }

    .career-options label {
      font-size: 18px;
      color: #444;
      cursor: pointer;
      display: flex;
      align-items: center;
    }

    button {
      background: linear-gradient(135deg, #2575fc, #6a11cb);
      color: white;
      padding: 12px 30px;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      font-size: 16px;
      margin-top: 20px;
      transition: 0.3s;
    }
    button:hover {
      background: linear-gradient(135deg, #1a5edb, #2575fc);
      transform: scale(1.05);
    }

    .hidden { display: none; }

    .result, .resources {
      background: #f9fbff;
      padding: 25px;
      border-radius: 15px;
      margin-top: 20px;
      box-shadow: inset 0 0 10px rgba(0,0,0,0.05);
      text-align: left;
    }

    ul { 
      padding-left: 20px; 
      list-style: none; 
      gap: 8px; 
    }
    li::before { 
      content: "✔ "; 
      color: #2575fc; 
      font-weight: bold; 
    }

    a {
      color: #2575fc;
      text-decoration: none;
      transition: 0.2s;
    }
    a:hover { text-decoration: underline; }

    .insights {
      margin-top: 20px;
      padding: 20px;
      border-left: 5px solid #2575fc;
      background: #eef5ff;
      border-radius: 10px;
    }
    .insights h4 {
      color: #2575fc;
      margin-bottom: 10px;
    }
    .story {
      margin-top: 10px;
      padding: 10px;
      background: white;
      border-radius: 8px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.08);
    }
    .story strong {
      color: #333;
    }
  </style>
</head>
<body>  

<!-- Homepage -->
<div class="container" id="homepage">
  <header>AI Career & Skills Advisor</header>
  <h2>Discover Your Perfect Career Path</h2>
  <p>Get personalized recommendations for Coding, Medical, Engineering, or Defence.</p>
  <button onclick="showForm()">Get Started</button>
</div>  

<!-- Input Form -->
<div class="container hidden" id="formpage">
  <header>Select Your Career Interest</header>
  <div class="career-options">
    <label><input type="radio" name="career" value="Coding"> 💻 Coding</label>
    <label><input type="radio" name="career" value="Medical"> 🩺 Medical</label>
    <label><input type="radio" name="career" value="Engineering"> ⚙ Engineering</label>
    <label><input type="radio" name="career" value="Defence"> 🪖 Defence</label>
  </div>
  <button onclick="generateCareer()">Generate Career Path</button>
</div>  

<!-- Results -->
<div class="container hidden" id="resultpage">
  <header>Your Personalized Career Path</header>
  <div class="result" id="careerResult"></div>
  <button onclick="showResources()">📚 View Resources & Insights</button><br>
  <button onclick="restart()">🔄 Start Again</button>
</div>  

<!-- Resources -->
<div class="container hidden" id="resourcepage">
  <header>Recommended Study Resources & Insights</header>
  <div class="resources" id="resourceLinks"></div>
  <button onclick="restart()">🔄 Start Again</button>
</div>

<script>
function showForm() {
  document.getElementById('homepage').classList.add('hidden');
  document.getElementById('formpage').classList.remove('hidden');
}

function generateCareer() {
  const choice = document.querySelector('input[name="career"]:checked');
  if (!choice) {
    alert("Please select a career option.");
    return;
  }
  const career = choice.value;
  let roadmap = "";

  if (career === "Coding") 
    roadmap = `<ul>
      <li>Start with basics: Python, C++ or Java</li>
      <li>Understand OOP & Problem Solving</li>
      <li>Master Data Structures & Algorithms</li>
      <li>Work on mini-projects & GitHub profile</li>
      <li>Learn Web Development (HTML, CSS, JS, React)</li>
      <li>Explore AI, Machine Learning & Cloud Computing</li>
      <li>Internships & Competitive Programming practice</li>
      <li>Build strong portfolio with real-world projects</li>
    </ul>`;

  if (career === "Medical") 
    roadmap = `<ul>
      <li>Prepare for NEET/Other Medical Entrance Exams</li>
      <li>Study core subjects: Physics, Chemistry, Biology</li>
      <li>Pursue MBBS from recognized college</li>
      <li>Choose specialization (Cardiology, Pediatrics, Surgery, etc.)</li>
      <li>Hands-on Clinical Practice & Internships</li>
      <li>Appear for PG exams (NEET PG/USMLE/PLAB)</li>
      <li>Join Research, Hospitals or Start Practice</li>
      <li>Continue Lifelong Learning through CME & Journals</li>
    </ul>`;

  if (career === "Engineering") 
    roadmap = `<ul>
      <li>Prepare for JEE/State Entrance Exams</li>
      <li>Choose specialization (Mechanical, Civil, CS, ECE, etc.)</li>
      <li>Focus on Core Subjects & Laboratory Work</li>
      <li>Work on Mini & Major Projects</li>
      <li>Do Internships & Industrial Training</li>
      <li>Learn CAD, MATLAB, or domain-specific tools</li>
      <li>Explore AI, Robotics, IoT, Renewable Energy</li>
      <li>Prepare for GATE/Higher Studies or Placements</li>
    </ul>`;

  if (career === "Defence") 
    roadmap = `<ul>
      <li>Prepare for NDA/CDS/AFCAT/Indian Navy exams</li>
      <li>Focus on Physical Fitness & Medical Standards</li>
      <li>Develop Leadership & Discipline qualities</li>
      <li>Attend SSB Interviews & Psychological Tests</li>
      <li>Undergo Military Training at Academies (IMA, NDA, OTA, INA)</li>
      <li>Choose specialization: Army, Navy, Air Force, Coast Guard</li>
      <li>Serve in National Defence with honor & dedication</li>
      <li>Opportunities for higher ranks & UN missions</li>
    </ul>`;

  document.getElementById('formpage').classList.add('hidden');
  document.getElementById('resultpage').classList.remove('hidden');
  document.getElementById('careerResult').innerHTML = `
    <h3>Recommended Career: ${career}</h3>
    <p><b>Roadmap:</b></p>${roadmap}
  `;

  window.selectedCareer = career;
}

function showResources() {
  const career = window.selectedCareer;
  let links = "";
  let insights = "";

  if (career === "Coding") {
    links = `<ul>
      <li><a href="https://www.coursera.org/specializations/python" target="_blank">Python Specialization - Coursera</a></li>
      <li><a href="https://www.geeksforgeeks.org/data-structures/" target="_blank">Data Structures - GeeksforGeeks</a></li>
      <li><a href="https://www.freecodecamp.org/" target="_blank">Full Stack Projects - freeCodeCamp</a></li>
      <li><a href="https://www.kaggle.com/" target="_blank">Machine Learning - Kaggle</a></li>
    </ul>`;
    insights = `
      <div class="insights">
        <h4>💡 Extra Insights</h4>
        <p><b>Average Salary:</b> ₹6–25 LPA (India), $70k–$150k (abroad)</p>
        <p><b>Entrance Path:</b> No single exam, but skills proven via coding contests, internships & projects.</p>
        <div class="story"><strong>Success Story:</strong> Sundar Pichai, CEO of Google, started as a coder from IIT Kharagpur and rose to lead one of the biggest tech companies.</div>
      </div>`;
  }

  if (career === "Medical") {
    links = `<ul>
      <li><a href="https://neet.nta.nic.in/" target="_blank">NEET Official Portal</a></li>
      <li><a href="https://www.khanacademy.org/science/health-and-medicine" target="_blank">Medical Concepts - Khan Academy</a></li>
      <li><a href="https://www.practo.com/healthfeed" target="_blank">Practo Health Articles</a></li>
      <li><a href="https://www.nejm.org/" target="_blank">New England Journal of Medicine</a></li>
    </ul>`;
    insights = `
      <div class="insights">
        <h4>💡 Extra Insights</h4>
        <p><b>Average Salary:</b> ₹8–30 LPA (specialists higher), $100k+ abroad</p>
        <p><b>Entrance Path:</b> NEET UG, AIIMS, USMLE (for abroad practice).</p>
        <div class="story"><strong>Success Story:</strong> Dr. Devi Shetty, a renowned cardiac surgeon, made affordable heart surgeries possible in India through Narayana Health.</div>
      </div>`;
  }

  if (career === "Engineering") {
    links = `<ul>
      <li><a href="https://nptel.ac.in/" target="_blank">Engineering Courses - NPTEL</a></li>
      <li><a href="https://www.coursera.org/browse/engineering" target="_blank">Engineering Specializations - Coursera</a></li>
      <li><a href="https://www.khanacademy.org/science" target="_blank">Math & Science - Khan Academy</a></li>
      <li><a href="https://www.udemy.com/courses/development/" target="_blank">Practical Projects - Udemy</a></li>
    </ul>`;
    insights = `
      <div class="insights">
        <h4>💡 Extra Insights</h4>
        <p><b>Average Salary:</b> ₹5–20 LPA depending on branch and company.</p>
        <p><b>Entrance Path:</b> JEE Mains/Advanced, GATE, GRE (for higher studies abroad).</p>
        <div class="story"><strong>Success Story:</strong> Dr. A.P.J. Abdul Kalam, an Aerospace Engineer, became the "Missile Man of India" and later the President of India.</div>
      </div>`;
  }

  if (career === "Defence") {
    links = `<ul>
      <li><a href="https://www.upsc.gov.in/" target="_blank">NDA/CDS Official UPSC Website</a></li>
      <li><a href="https://afcat.cdac.in/" target="_blank">AFCAT Official Portal</a></li>
      <li><a href="https://www.joinindiannavy.gov.in/" target="_blank">Indian Navy Careers</a></li>
      <li><a href="https://joinindianarmy.nic.in/" target="_blank">Indian Army Recruitment</a></li>
    </ul>`;
    insights = `
      <div class="insights">
        <h4>💡 Extra Insights</h4>
        <p><b>Average Salary:</b> ₹8–18 LPA with perks (housing, pension, allowances).</p>
        <p><b>Entrance Path:</b> NDA, CDS, AFCAT, SSB Interview.</p>
        <div class="story"><strong>Success Story:</strong> Captain Vikram Batra, Param Vir Chakra awardee, became a symbol of courage in the Kargil War with his famous words "Yeh Dil Maange More".</div>
      </div>`;
  }

  document.getElementById('resultpage').classList.add('hidden');
  document.getElementById('resourcepage').classList.remove('hidden');
  document.getElementById('resourceLinks').innerHTML = links + insights;
}

function restart() {
  document.getElementById('resourcepage').classList.add('hidden');
  document.getElementById('resultpage').classList.add('hidden');
  document.getElementById('homepage').classList.remove('hidden');
}
</script>

</body>
</html>
