<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Mutant Academy V4.3.1</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: radial-gradient(circle at center, #0a0f1c, #000);
      color: #fff;
      text-align: center;
    }
    #game {
      max-width: 480px;
      margin: auto;
      padding: 20px;
    }
    .screen { display: none; }
    .active { display: block; animation: fadeIn 0.8s; }
    @keyframes fadeIn { from {opacity: 0;} to {opacity: 1;} }
    button {
      margin: 10px;
      padding: 10px 20px;
      font-size: 16px;
      border-radius: 6px;
      border: none;
      cursor: pointer;
      background: #3498db;
      color: #fff;
      transition: transform 0.2s, background 0.2s;
    }
    button:hover { transform: scale(1.1); background: #2980b9; }
    .health-bar {
      height: 20px;
      background: red;
      transition: width 0.5s;
    }
    .bar-container {
      width: 100%;
      background: #333;
      border: 1px solid #555;
      margin-bottom: 10px;
    }
    .float-dmg {
      position: absolute;
      color: yellow;
      font-weight: bold;
      animation: floatUp 1s ease-out forwards;
      pointer-events: none;
    }
    @keyframes floatUp {
      from { opacity: 1; transform: translateY(0); }
      to { opacity: 0; transform: translateY(-40px); }
    }
    .enemy-hit { animation: flashRed 0.3s; }
    @keyframes flashRed {
      0% { filter: brightness(1) contrast(1); }
      50% { filter: brightness(2) contrast(2) hue-rotate(-50deg); }
      100% { filter: brightness(1) contrast(1); }
    }
  </style>
</head>
<body>
  <div id="game">
    <!-- Écran d'accueil -->
    <div id="start" class="screen active">
      <h1>🎓 Mutant Academy</h1>
      <p>Choisis ta difficulté :</p>
      <button onclick="setDifficulty('easy')">Facile</button>
      <button onclick="setDifficulty('normal')">Normal</button>
      <button onclick="setDifficulty('hard')">Difficile</button>
    </div>

    <!-- Écran des pouvoirs -->
    <div id="powers" class="screen">
      <h2>Choisis ton pouvoir</h2>
      <div id="power-options"></div>
    </div>

    <!-- Écran de combat -->
    <div id="battle" class="screen">
      <h2 id="enemyName"></h2>
      <div class="bar-container"><div id="enemyHP" class="health-bar"></div></div>
      <div class="bar-container"><div id="playerHP" class="health-bar"></div></div>
      <p id="battleLog"></p>
      <button onclick="attack()">⚡ Attaquer</button>
    </div>

    <!-- Écran de fin -->
    <div id="end" class="screen">
      <h2 id="endMessage"></h2>
      <button onclick="restart()">Rejouer</button>
    </div>
  </div>

  <!-- Sons -->
  <audio id="soundAttack" src="https://actions.google.com/sounds/v1/impacts/wood_plank_flicks.ogg"></audio>
  <audio id="soundHit" src="https://actions.google.com/sounds/v1/impacts/thud.ogg"></audio>
  <audio id="soundWin" src="https://actions.google.com/sounds/v1/cartoon/clang_and_wobble.ogg"></audio>
  <audio id="soundLose" src="https://actions.google.com/sounds/v1/cartoon/woodpecker_pecking.ogg"></audio>

  <script>
    const screens = {
      start: document.getElementById("start"),
      powers: document.getElementById("powers"),
      battle: document.getElementById("battle"),
      end: document.getElementById("end"),
    };

    let difficulty, playerHP, playerMaxHP = 100, enemyHP, enemyMaxHP, enemies, currentEnemyIndex = 0, power;

    const powerList = ["🔥 Feu", "❄️ Glace", "🧠 Télépathie", "⚡ Foudre", "🪨 Métal", "🌑 Ombre"];

    function showScreen(name) {
      for (let s in screens) screens[s].classList.remove("active");
      screens[name].classList.add("active");
    }

    function setDifficulty(level) {
      difficulty = level;
      if (level === "easy") enemies = [{name:"Sentinelle", hp:40},{name:"Sabretooth", hp:60},{name:"Magneto", hp:80}];
      if (level === "normal") enemies = [{name:"Sentinelle", hp:60},{name:"Sabretooth", hp:80},{name:"Magneto", hp:100}];
      if (level === "hard") enemies = [{name:"Sentinelle", hp:80},{name:"Sabretooth", hp:100},{name:"Magneto", hp:120}];
      playerHP = playerMaxHP;
      generatePowers();
      showScreen("powers");
    }

    function generatePowers() {
      const container = document.getElementById("power-options");
      container.innerHTML = "";
      powerList.forEach(p => {
        const btn = document.createElement("button");
        btn.textContent = p;
        btn.onclick = () => choosePower(p);
        container.appendChild(btn);
      });
    }

    function choosePower(p) {
      power = p;
      currentEnemyIndex = 0;
      startBattle();
    }

    function startBattle() {
      const enemy = enemies[currentEnemyIndex];
      enemyMaxHP = enemy.hp;
      enemyHP = enemyMaxHP;
      document.getElementById("enemyName").textContent = "👾 " + enemy.name;
      updateBars();
      document.getElementById("battleLog").textContent = "Le combat commence ! Prépare ton pouvoir " + power;
      showScreen("battle");
    }

    function updateBars() {
      document.getElementById("enemyHP").style.width = (enemyHP/enemyMaxHP*100) + "%";
      document.getElementById("playerHP").style.width = (playerHP/playerMaxHP*100) + "%";
    }

    function floatDamage(amount, targetId) {
      const el = document.createElement("div");
      el.className = "float-dmg";
      el.textContent = "-" + amount;
      const target = document.getElementById(targetId);
      const rect = target.getBoundingClientRect();
      el.style.left = (rect.left + rect.width/2) + "px";
      el.style.top = (rect.top - 20) + "px";
      document.body.appendChild(el);
      setTimeout(() => el.remove(), 1000);
    }

    function attack() {
      const soundAttack = document.getElementById("soundAttack");
      const soundHit = document.getElementById("soundHit");
      const enemyEl = document.getElementById("enemyName");

      let dmg = Math.floor(Math.random() * 15) + 5;
      enemyHP -= dmg;
      if (enemyHP < 0) enemyHP = 0;
      floatDamage(dmg, "enemyHP");
      enemyEl.classList.add("enemy-hit");
      soundAttack.play();
      setTimeout(()=>enemyEl.classList.remove("enemy-hit"), 300);
      document.getElementById("battleLog").textContent = "Tu infliges " + dmg + " dégâts à l'ennemi.";
      updateBars();

      if (enemyHP <= 0) {
        currentEnemyIndex++;
        if (currentEnemyIndex >= enemies.length) {
          document.getElementById("endMessage").textContent = "🏆 Félicitations ! Tu as vaincu Magneto et tu fais désormais partie des X-Men !";
          document.getElementById("soundWin").play();
          showScreen("end");
        } else {
          setTimeout(startBattle, 1000);
        }
        return;
      }

      // riposte ennemie
      setTimeout(() => {
        let enemyDmg = Math.floor(Math.random() * 12) + 3;
        playerHP -= enemyDmg;
        if (playerHP < 0) playerHP = 0;
        floatDamage(enemyDmg, "playerHP");
        soundHit.play();
        document.getElementById("battleLog").textContent = "L'ennemi riposte et inflige " + enemyDmg + " dégâts.";
        updateBars();

        if (playerHP <= 0) {
          document.getElementById("endMessage").textContent = "💀 Défaite... Mais tu pourras toujours t'entraîner à l'Académie.";
          document.getElementById("soundLose").play();
          showScreen("end");
        }
      }, 1000);
    }

    function restart() {
      showScreen("start");
    }
  </script>
</body>
</html>
