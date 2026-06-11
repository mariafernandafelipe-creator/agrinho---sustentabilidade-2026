# agrinho---sustentabilidade-2026// App.js
agro-app/
│── index.html
│── style.css
│── script.js
│── README.md
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AgroApp Sustentável</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>AgroApp Sustentável</h1>
    <p>Cuide do solo, aumente o lucro, preserve o futuro.</p>
  </header>

  <main>
    <section id="feedback">
      <h2>Retroalimentação do Solo</h2>
      <p>Insira dados sobre seu solo e receba recomendações inteligentes.</p>
      <form id="soilForm">
        <label for="ph">pH do solo:</label>
        <input type="number" id="ph" name="ph" step="0.1" required>

        <label for="nutrientes">Nutrientes principais:</label>
        <input type="text" id="nutrientes" name="nutrientes" placeholder="Ex: Nitrogênio, Fósforo">

        <button type="submit">Gerar Feedback</button>
      </form>
      <div id="result"></div>
    </section>
  </main>

  <footer>
    <p>Projeto Agrinho 2026 - Maria</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
:root {
  --blue: #007BFF;
  --light: #F8F9FA;
  --cyan: #17A2B8;
  --teal: #20C997;
}

body {
  font-family: Arial, sans-serif;
  background-color: var(--light);
  color: #333;
  margin: 0;
  padding: 0;
}

header {
  background: var(--blue);
  color: white;
  text-align: center;
  padding: 2rem;
}

h1 {
  margin: 0;
}

main {
  padding: 2rem;
}

button {
  background: var(--teal);
  color: white;
  border: none;
  padding: 0.7rem 1.2rem;
  cursor: pointer;
  border-radius: 5px;
}

button:hover {
  background: var(--cyan);
}

#result {
  margin-top: 1rem;
  padding: 1rem;
  background: var(--cyan);
  color: white;
  border-radius: 5px;
}
document.getElementById("soilForm").addEventListener("submit", function(event) {
  event.preventDefault();

  const ph = document.getElementById("ph").value;
  const nutrientes = document.getElementById("nutrientes").value;

  let feedback = "";

  if (ph < 5.5) {
    feedback += "⚠️ O solo está ácido. Considere aplicar calcário. ";
  } else if (ph > 7.5) {
    feedback += "⚠️ O solo está alcalino. Avalie correções com matéria orgânica. ";
  } else {
    feedback += "✅ O pH está adequado para a maioria das culturas. ";
  }

  feedback += `Nutrientes informados: ${nutrientes}.`;

  document.getElementById("result").innerText = feedback;
});
