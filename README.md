# viedeopalnner
Yt viedeo Sammler
<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>YT Ideen Sortierer</title>
<style>
  /* Grundlayout */
  body {
    margin: 0; padding: 0;
    background: #121212;
    color: #eee;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: flex-start;
    padding: 40px 20px;
  }
  #container {
    width: 100%;
    max-width: 700px;
    background: #1e1e1e;
    border-radius: 12px;
    box-shadow: 0 0 25px #ff6f00aa;
    padding: 30px 40px;
  }
  h1, h2, h3 {
    margin: 0 0 20px 0;
    font-weight: 700;
    color: #ffb347;
    text-align: center;
    font-family: 'Orbitron', sans-serif;
  }
  /* Login */
  #loginSection {
    display: flex;
    flex-direction: column;
    gap: 15px;
    max-width: 400px;
    margin: 0 auto;
  }
  input[type=text], input[type=password], select, textarea {
    padding: 14px 18px;
    border-radius: 8px;
    border: none;
    font-size: 1rem;
    background: #2b2b2b;
    color: #eee;
    box-sizing: border-box;
    transition: background 0.3s;
  }
  input[type=text]:focus, input[type=password]:focus, select:focus, textarea:focus {
    outline: none;
    background: #3a3a3a;
  }
  button {
    background: linear-gradient(45deg, #ff8c00, #ffb347);
    border: none;
    color: #222;
    font-weight: 700;
    padding: 14px 0;
    border-radius: 10px;
    cursor: pointer;
    font-size: 1.1rem;
    transition: background 0.3s;
  }
  button:hover {
    background: linear-gradient(45deg, #ffb347, #ff8c00);
    color: #111;
  }
  /* App Section */
  #appSection {
    display: none;
    flex-direction: column;
  }
  #headerRow {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 25px;
  }
  #displayUser {
    font-weight: 700;
    font-size: 1.3rem;
  }
  #logoutBtn {
    max-width: 110px;
  }
  /* Add idea row */
  #addIdeaRow {
    display: flex;
    gap: 15px;
    margin-bottom: 25px;
  }
  #addIdeaRow input[type=text] {
    flex: 2;
  }
  #addIdeaRow select {
    flex: 1;
  }
  #addIdeaRow button {
    flex: 1;
  }
  /* Filter row */
  #filterRow {
    margin-bottom: 25px;
  }
  #filterSelect {
    width: 100%;
    max-width: 250px;
    padding: 12px 15px;
  }
  /* Ideen Liste */
  #ideasList {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }
  .ideaCard {
    background: #292929;
    padding: 18px 20px;
    border-radius: 14px;
    box-shadow: 0 0 10px #ff9e1b88;
    position: relative;
  }
  .ideaCard h4 {
    margin: 0 0 6px 0;
    color: #ffb347;
    font-family: 'Orbitron', sans-serif;
  }
  .ideaCategory {
    font-weight: 600;
    color: #ff8c00;
    margin-bottom: 8px;
  }
  .ideaDate {
    font-size: 0.85rem;
    color: #ffb347aa;
    margin-bottom: 12px;
  }
  .ideaNotes {
    width: 100%;
    min-height: 60px;
    background: #222;
    border-radius: 10px;
    padding: 10px;
    resize: vertical;
    color: #eee;
    font-size: 0.95rem;
    border: none;
  }
  .deleteBtn {
    position: absolute;
    top: 16px;
    right: 16px;
    background: #bb241b;
    border: none;
    padding: 6px 12px;
    border-radius: 12px;
    color: white;
    font-weight: 700;
    cursor: pointer;
    transition: background 0.3s;
  }
  .deleteBtn:hover {
    background: #8b1913;
  }
  /* Responsive */
  @media (max-width: 520px) {
    #addIdeaRow {
      flex-direction: column;
    }
    #addIdeaRow button {
      flex: unset;
      width: 100%;
    }
    #filterSelect {
      max-width: 100%;
    }
    #container {
      padding: 25px 20px;
    }
  }
</style>
</head>
<body>

<div id="container">
  <!-- LOGIN -->
  <section id="loginSection">
    <h1>YT Ideen Sortierer</h1>
    <input type="text" id="loginUser" placeholder="Benutzername" autocomplete="username" />
    <input type="password" id="loginPass" placeholder="Passwort" autocomplete="current-password" />
    <button id="loginBtn">Einloggen</button>
    <p style="text-align:center; margin-top:15px; color:#ffb347a0; font-size:0.9rem;">
      Benutzer: <b>benedeto</b> | Passwort: <b>Benedeto</b>
    </p>
  </section>

  <!-- APP -->
  <section id="appSection" style="display:none; flex-direction: column;">
    <div id="headerRow">
      <div>Willkommen, <span id="displayUser"></span>!</div>
      <button id="logoutBtn">Logout</button>
    </div>

    <div id="addIdeaRow">
      <input type="text" id="ideaInput" placeholder="Neue Idee eingeben..." />
      <select id="categorySelect">
        <option value="Road To 10 Millionen">Road To 10 Millionen</option>
        <option value="Tipps und Tricks">Tipps und Tricks</option>
        <option value="Sonstiges">Sonstiges</option>
      </select>
      <button id="addIdeaBtn">➕ Idee</button>
    </div>

    <div id="filterRow">
      <select id="filterSelect">
        <option value="Alle">Alle Kategorien</option>
        <option value="Road To 10 Millionen">Road To 10 Millionen</option>
        <option value="Tipps und Tricks">Tipps und Tricks</option>
        <option value="Sonstiges">Sonstiges</option>
      </select>
    </div>

    <div id="ideasList">
      <!-- Ideen erscheinen hier -->
    </div>
  </section>
</div>

<script>
  const loginSection = document.getElementById('loginSection');
  const appSection = document.getElementById('appSection');
  const loginBtn = document.getElementById('loginBtn');
  const logoutBtn = document.getElementById('logoutBtn');
  const displayUser = document.getElementById('displayUser');
  const ideaInput = document.getElementById('ideaInput');
  const categorySelect = document.getElementById('categorySelect');
  const addIdeaBtn = document.getElementById('addIdeaBtn');
  const filterSelect = document.getElementById('filterSelect');
  const ideasList = document.getElementById('ideasList');

  let ideas = [];
  let currentUser = null;

  // Login-Funktion
  loginBtn.addEventListener('click', () => {
    const user = document.getElementById('loginUser').value.trim();
    const pass = document.getElementById('loginPass').value;

    if(user.toLowerCase() === 'benedeto' && pass === 'Benedeto') {
      currentUser = user;
      loginSection.style.display = 'none';
      appSection.style.display = 'flex';
      displayUser.textContent = user;
      renderIdeas();
    } else {
      alert('Falscher Benutzername oder Passwort!');
    }
  });

  logoutBtn.addEventListener('click', () => {
    currentUser = null;
    ideas = [];
    ideaInput.value = '';
    loginSection.style.display = 'flex';
    appSection.style.display = 'none';
  });

  addIdeaBtn.addEventListener('click', () => {
    const text = ideaInput.value.trim();
    const category = categorySelect.value;
    if(text === '') {
      alert('Bitte gib eine Idee ein!');
      return;
    }
    const date = new Date().toLocaleDateString('de-DE');
    ideas.push({text, category, notes: '', date});
    ideaInput.value = '';
    renderIdeas();
  });

  filterSelect.addEventListener('change', renderIdeas);

  function deleteIdea(index) {
    if(confirm('Willst du diese Idee wirklich löschen?')) {
      ideas.splice(index, 1);
      renderIdeas();
    }
  }

  function updateNotes(index, e) {
    ideas[index].notes = e.target.value;
  }

  function renderIdeas() {
    ideasList.innerHTML = '';
    const filter = filterSelect.value;

    const filtered = ideas.filter(idea => filter === 'Alle' || idea.category === filter);

    if(filtered.length === 0) {
      ideasList.innerHTML = '<p style="text-align:center; opacity:0.6;">Keine Ideen gefunden.</p>';
      return;
    }

    filtered.forEach((idea, idx) => {
      // Index im Originalarray, nicht gefiltert
      const originalIndex = ideas.indexOf(idea);

      const card = document.createElement('div');
      card.className = 'ideaCard';

      card.innerHTML = `
        <h4>${idea.text}</h4>
        <div class="ideaCategory">Kategorie: ${idea.category}</div>
        <div class="ideaDate">📅 Hinzugefügt am: ${idea.date}</div>
        <textarea class="ideaNotes" placeholder="Notizen...">${idea.notes}</textarea>
        <button class="deleteBtn" title="Löschen">🗑️</button>
      `;

      card.querySelector('.deleteBtn').addEventListener('click', () => deleteIdea(originalIndex));
      card.querySelector('.ideaNotes').addEventListener('input', (e) => updateNotes(originalIndex, e));

      ideasList.appendChild(card);
    });
  }
</script>

</body>
</html>
