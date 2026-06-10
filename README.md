# agrinho---sustentabilidade-2026// App.js
import React from "react";
import "./App.css";

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <h1>Agrinho 2026 - AgroApp</h1>
        <p>
          Cuidando do solo, unindo grandes e pequenos agricultores com
          consciência e lucro sustentável.
        </p>
        <button className="main-button">Começar</button>
      </header>
    </div>
  );
}

export default App;
/* App.css */
.App {
  text-align: center;
  background-color: #e0f7fa; /* light cyan */
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  color: #004d40; /* teal escuro */
  font-family: "Segoe UI", sans-serif;
}

.App-header h1 {
  color: #0288d1; /* blue */
}

.App-header p {
  color: #00796b; /* teal */
}

.main-button {
  background-color: #00acc1; /* cyan */
  border: none;
  padding: 12px 24px;
  margin-top: 20px;
  border-radius: 8px;
  color: white;
  font-size: 16px;
  cursor: pointer;
  transition: 0.3s;
}

.main-button:hover {
  background-color: #00838f; /* teal mais escuro */
}
// FarmerForm.js
import React, { useState } from "react";

function FarmerForm() {
  const [formData, setFormData] = useState({
    nome: "",
    tipo: "pequeno",
    regiao: ""
  });

  const handleChange = (e) => {
    setFormData({ ...formData, [e.target.name]: e.target.value });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log("Dados cadastrados:", formData);
    alert("Cadastro realizado com sucesso!");
  };

  return (
    <form onSubmit={handleSubmit} className="farmer-form">
      <h2>Cadastro de Agricultor</h2>
      <label>
        Nome:
        <input
          type="text"
          name="nome"
          value={formData.nome}
          onChange={handleChange}
          required
        />
      </label>

      <label>
        Tipo de Agricultor:
        <select
          name="tipo"
          value={formData.tipo}
          onChange={handleChange}
        >
          <option value="pequeno">Pequeno</option>
          <option value="grande">Grande</option>
        </select>
      </label>

      <label>
        Região:
        <input
          type="text"
          name="regiao"
          value={formData.regiao}
          onChange={handleChange}
          required
        />
      </label>

      <button type="submit" className="main-button">Cadastrar</button>
    </form>
  );
}

export default FarmerForm;
.farmer-form {
  background-color: #e0f7fa; /* light cyan */
  padding: 20px;
  border-radius: 10px;
  max-width: 400px;
  margin: auto;
  color: #004d40; /* teal escuro */
}

.farmer-form h2 {
  color: #0288d1; /* blue */
}

.farmer-form label {
  display: block;
  margin: 10px 0;
}

.farmer-form input,
.farmer-form select {
  width: 100%;
  padding: 8px;
  margin-top: 5px;
  border: 1px solid #00acc1; /* cyan */
  border-radius: 6px;
}

.farmer-form button {
  margin-top: 15px;
}
// SoilMonitor.js
import React, { useState, useEffect } from "react";

function SoilMonitor() {
  const [data, setData] = useState({ ph: 6.5, umidade: 45, temperatura: 22 });

  useEffect(() => {
    // Simulação: em um app real, os dados viriam da nuvem
    const interval = setInterval(() => {
      setData({
        ph: (Math.random() * (7 - 5) + 5).toFixed(2),
        umidade: Math.floor(Math.random() * 100),
        temperatura: Math.floor(Math.random() * 35)
      });
    }, 5000);
    return () => clearInterval(interval);
  }, []);

  return (
    <div className="monitor">
      <h2>Monitoramento do Solo</h2>
      <p>pH: {data.ph}</p>
      <p>Umidade: {data.umidade}%</p>
      <p>Temperatura: {data.temperatura}°C</p>
    </div>
  );
}

export default SoilMonitor;
