# bible-writing-tracker
// Writing My Way Through Scripture GPT - Digital Tracker Script (No-Cost Version)
// Using HTML + JavaScript (can be hosted locally or on a free site like GitHub Pages)

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Writing My Way Through Scripture</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f9;
      color: #333;
      padding: 20px;
    }
    h1, h2 {
      color: #4A7C59;
    }
    .progress {
      background: #ddd;
      border-radius: 10px;
      overflow: hidden;
      margin-bottom: 10px;
    }
    .progress-bar {
      height: 20px;
      background: #4A7C59;
      text-align: center;
      color: #fff;
      line-height: 20px;
    }
    input, button {
      padding: 10px;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <h1>📖 Writing My Way Through Scripture</h1>
  <h2>A Handwritten Journey of Faith, Wisdom and Grace</h2>

  <label>Enter completed verses:</label><br>
  <input type="number" id="versesInput" placeholder="e.g., 25" min="1">
  <button onclick="addVerses()">Add</button>
  <button onclick="resetProgress()">Reset</button>
  <button onclick="printTracker()">Print Tracker</button>

  <h3>Progress:</h3>
  <div class="progress">
    <div class="progress-bar" id="progressBar" style="width: 0%">0%</div>
  </div>
  <p id="encouragement"></p>

  <script>
    const TOTAL_VERSES = 31102; // Total verses in the Bible
    let writtenVerses = JSON.parse(localStorage.getItem('writtenVerses')) || 0;

    function updateProgress() {
      const percent = Math.min(100, (writtenVerses / TOTAL_VERSES * 100).toFixed(2));
      document.getElementById('progressBar').style.width = percent + '%';
      document.getElementById('progressBar').innerText = percent + '%';

      let encouragement = '';
      if (percent >= 5) encouragement = '🙌 5% complete – You’re off to a strong start!';
      if (percent >= 10) encouragement = '✨ 10% in – Keep pressing forward!';
      if (percent >= 25) encouragement = '🌿 25% done – God is doing a new thing in you!';
      if (percent >= 50) encouragement = '🔥 50% – You’re halfway through His Word!';
      if (percent >= 75) encouragement = '🌈 75% – The finish line is in sight!';
      if (percent >= 100) encouragement = '🎉 100% – You’ve written through the entire Bible!';
      document.getElementById('encouragement').innerText = encouragement;
    }

    function addVerses() {
      const input = document.getElementById('versesInput');
      const verses = parseInt(input.value);
      if (!isNaN(verses)) {
        writtenVerses += verses;
        localStorage.setItem('writtenVerses', writtenVerses);
        input.value = '';
        updateProgress();
      }
    }

    function resetProgress() {
      if (confirm('Reset all progress?')) {
        writtenVerses = 0;
        localStorage.setItem('writtenVerses', writtenVerses);
        updateProgress();
      }
    }

    function printTracker() {
      window.print();
    }

    updateProgress();
  </script>
</body>
</html>
git add .
git commit -m "Add badge system, refine progress logic, style enhancements"
git push origin main
git pull origin main
"added badge milestones and chapter tracking enhancements"
