<!-- Updated progress tracker logic -->
<script>
  let totalVerses = 31102;
  let completedVerses = 0;
  let completedChapters = 0;
  let badges = [];

  function updateProgress() {
    const verseInput = document.getElementById("verseInput");
    const chapterInput = document.getElementById("chapterInput");
    const progressBar = document.getElementById("progressBar");
    const progressText = document.getElementById("progressText");
    const milestoneText = document.getElementById("milestoneText");
    const badgeContainer = document.getElementById("badgeContainer");

    completedVerses = parseInt(verseInput.value) || 0;
    completedChapters = parseInt(chapterInput.value) || 0;
    const progress = Math.min((completedVerses / totalVerses) * 100, 100);
    progressBar.style.width = progress + "%";
    progressText.innerText = `You have completed ${progress.toFixed(2)}% of the Bible.`;

    // Milestones for verses (every 5%)
    if (progress >= 5 && !badges.includes("5%")) grantBadge("5%", badgeContainer);
    if (progress >= 10 && !badges.includes("10%")) grantBadge("10%", badgeContainer);
    if (progress >= 25 && !badges.includes("25%")) grantBadge("25%", badgeContainer);
    if (progress >= 50 && !badges.includes("50%")) grantBadge("50%", badgeContainer);
    if (progress >= 75 && !badges.includes("75%")) grantBadge("75%", badgeContainer);
    if (progress >= 100 && !badges.includes("100%")) grantBadge("100%", badgeContainer);

    // Milestones for chapters
    const chapterMilestones = [5, 10, 25, 40, 50, 75, 100];
    chapterMilestones.forEach(milestone => {
      if (completedChapters >= milestone && !badges.includes(`Chapter ${milestone}`)) {
        grantBadge(`Chapter ${milestone}`, badgeContainer);
      }
    });
  }

  function grantBadge(label, container) {
    const badge = document.createElement("div");
    badge.className = "badge";
    badge.innerText = `🏅 ${label} Milestone Reached!`;
    container.appendChild(badge);
    badges.push(label);
  }

  function resetTracker() {
    document.getElementById("verseInput").value = 0;
    document.getElementById("chapterInput").value = 0;
    document.getElementById("progressBar").style.width = "0%";
    document.getElementById("progressText").innerText = "You have completed 0% of the Bible.";
    document.getElementById("badgeContainer").innerHTML = "";
    badges = [];
  }
</script>
update mileson system
