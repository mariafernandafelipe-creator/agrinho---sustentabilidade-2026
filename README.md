
    <meta charset="UTF-8">
    <title>AgroSolo Consciente</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- CSS principal -->
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header class="topbar">
        <div class="logo">
            <span class="logo-icon">A</span>
            <span class="logo-text">AgroSolo Consciente</span>
        </div>
        <nav class="nav">
            <a href="#dashboard">Início</a>
            <a href="#analise">Análise do Solo</a>
            <a href="#sobre">Sobre o Projeto</a>
        </nav>
    </header>

    <main>
        <!-- SEÇÃO 1: Painel geral -->
        <section id="dashboard" class="section">
            <h1>Cuidado inteligente com o solo</h1>
            <p class="subtitle">
                Ajude pequenos e grandes produtores a usar melhor o solo, 
                reduzindo desperdícios e aumentando o lucro com consciência.
            </p>

            <div class="cards-grid">
                <div class="card">
                    <h2>Resumo da propriedade</h2>
                    <p>Adicione áreas de plantio e acompanhe o estado do solo.</p>
                    <button class="btn-primary" onclick="abrirFormularioArea()">
                        + Adicionar área de plantio
                    </button>
                </div>

                <div class="card">
                    <h2>Indicadores de sustentabilidade</h2>
                    <ul class="indicators-list">
                        <li><span class="tag tag-ok"></span> Uso de adubo mais eficiente</li>
                        <li><span class="tag tag-mid"></span> Economia de água</li>
                        <li><span class="tag tag-alert"></span> Risco de compactação do solo</li>
                    </ul>
                </div>

                <div class="card">
                    <h2>Retroalimentação inteligente</h2>
                    <p>
                        O app gera recomendações simples para você ajustar o manejo, 
                        sem desperdiçar insumos e mantendo a produtividade.
                    </p>
                    <button class="btn-secondary" onclick="gerarRelatorioGeral()">
                        Gerar relatório geral
                    </button>
                </div>
            </div>
        </section>

        <!-- SEÇÃO 2: Análise do solo -->
        <section id="analise" class="section">
            <h2>Análise rápida do solo</h2>
            <p class="subtitle">
                Preencha os dados básicos da área e receba recomendações iniciais de manejo.
            </p>

            <form id="formSolo" class="form-card" onsubmit="analisarSolo(event)">
                <div class="form-row">
                    <div class="form-field">
                        <label for="nomeArea">Nome da área</label>
                        <input type="text" id="nomeArea" placeholder="Ex: Talhão 1 - Soja">
                    </div>

                    <div class="form-field">
                        <label for="tamanhoArea">Tamanho da área (ha)</label>
                        <input type="number" id="tamanhoArea" placeholder="Ex: 5">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-field">
                        <label for="tipoSolo">Tipo de solo</label>
                        <select id="tipoSolo">
                            <option value="">Selecione...</option>
                            <option value="arenoso">Arenoso</option>
                            <option value="argiloso">Argiloso</option>
                            <option value="misturado">Misturado</option>
                        </select>
                    </div>

                    <div class="form-field">
                        <label for="phSolo">pH do solo</label>
                        <input type="number" step="0.1" id="phSolo" placeholder="Ex: 5.5">
                    </div>

                    <div class="form-field">
                        <label for="matOrganica">Matéria orgânica (%)</label>
                        <input type="number" step="0.1" id="matOrganica" placeholder="Ex: 2.5">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-field">
                        <label for="cultura">Cultura principal</label>
                        <input type="text" id="cultura" placeholder="Ex: Milho, Soja, Feijão...">
                    </div>

                    <div class="form-field">
                        <label for="irrigacao">Tem irrigação?</label>
                        <select id="irrigacao">
                            <option value="">Selecione...</option>
                            <option value="sim">Sim</option>
                            <option value="nao">Não</option>
                        </select>
                    </div>
                </div>

                <button type="submit" class="btn-primary full-width">
                    Gerar recomendações
                </button>
            </form>

            <div id="resultadoAnalise" class="result-card hidden">
                <h3>Recomendações iniciais para o solo</h3>
                <p id="resumoArea" class="result-summary"></p>
                <ul id="listaRecomendacoes" class="recomendations-list"></ul>
            </div>
        </section>

        <!-- SEÇÃO 3: Sobre o projeto -->
        <section id="sobre" class="section">
            <h2>Sobre o projeto Agrinho</h2>
            <p>
                Este aplicativo foi criado como projeto para o Agrinho, com o objetivo de
                apoiar pequenos e grandes agricultores a cuidar melhor dos seus solos.
            </p>
            <p>
                A ideia é usar dados simples da propriedade para gerar uma 
                <strong>retroalimentação</strong> sustentável: o produtor utiliza melhor 
                os insumos, gasta menos e mantém a produção com mais consciência ambiental.
            </p>
        </section>
    </main>

    <footer class="footer">
        <small>Projeto Agrinho · AgroSolo Consciente · 2026</small>
    </footer>

    <!-- JavaScript principal -->
    <script src="script.js"></script>
</body>
</html>
/* Paleta de cores (azul, light, cyan, teal) */
:root {
    --bg-dark: #020617;
    --bg-card: #020c1f;
    --accent-blue: #1d4ed8;
    --accent-cyan: #06b6d4;
    --accent-teal: #0d9488;
    --text-main: #e5e7eb;
    --text-muted: #9ca3af;
    --border-soft: rgba(148, 163, 184, 0.2);
    --radius-lg: 16px;
    --radius-md: 12px;
    --transition-fast: 0.2s ease;
    --shadow-soft: 0 18px 45px rgba(15, 23, 42, 0.7);
}

/* RESET SIMPLES */
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    background: radial-gradient(circle at top, #0f172a 0, #020617 45%, #000 100%);
    color: var(--text-main);
    min-height: 100vh;
}

/* TOPO */

.topbar {
    position: sticky;
    top: 0;
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 14px 7vw;
    background: rgba(2, 6, 23, 0.9);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border-soft);
}

.logo {
    display: flex;
    align-items: center;
    gap: 10px;
}

.logo-icon {
    width: 32px;
    height: 32px;
    border-radius: 999px;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, var(--accent-cyan), var(--accent-teal));
    font-weight: 700;
    color: #0b1120;
    font-size: 18px;
}

.logo-text {
    font-weight: 600;
    letter-spacing: 0.04em;
    font-size: 16px;
}

.nav {
    display: flex;
    gap: 20px;
    font-size: 14px;
}

.nav a {
    color: var(--text-muted);
    text-decoration: none;
    padding: 6px 10px;
    border-radius: 999px;
    transition: color var(--transition-fast), background var(--transition-fast);
}

.nav a:hover {
    color: #e5f3ff;
    background: rgba(37, 99, 235, 0.18);
}

/* SEÇÕES GERAIS */

main {
    padding: 32px 7vw 64px;
}

.section {
    max-width: 1100px;
    margin: 0 auto 48px;
}

.section h1,
.section h2 {
    font-weight: 650;
    letter-spacing: 0.03em;
}

.section h1 {
    font-size: 32px;
    margin-bottom: 10px;
}

.section h2 {
    font-size: 22px;
    margin-bottom: 8px;
}

.subtitle {
    color: var(--text-muted);
    font-size: 15px;
    max-width: 640px;
    margin-bottom: 24px;
}

/* CARDS */

.cards-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 18px;
}

.card,
.form-card,
.result-card {
    background: radial-gradient(circle at top left, #020c1f 0, #020617 45%);
    border-radius: var(--radius-lg);
    border: 1px solid var(--border-soft);
    padding: 18px 18px 20px;
    box-shadow: var(--shadow-soft);
    position: relative;
    overflow: hidden;
}

.card::before,
.form-card::before,
.result-card::before {
    content: "";
    position: absolute;
    inset: -40%;
    opacity: 0.18;
    background:
        radial-gradient(circle at 0% 0%, rgba(37, 99, 235, 0.32), transparent 50%),
        radial-gradient(circle at 100% 0%, rgba(8, 145, 178, 0.28), transparent 50%);
    pointer-events: none;
}

/* Para não afetar o conteúdo, usamos um wrapper */
.card > *,
.form-card > *,
.result-card > * {
    position: relative;
    z-index: 1;
}

/* LISTA DE INDICADORES */

.indicators-list {
    list-style: none;
    margin-top: 8px;
    display: flex;
    flex-direction: column;
    gap: 6px;
    font-size: 14px;
    color: var(--text-muted);
}

.tag {
    display: inline-block;
    width: 8px;
    height: 8px;
    border-radius: 999px;
    margin-right: 8px;
}

.tag-ok {
    background: var(--accent-teal);
}
.tag-mid {
    background: var(--accent-cyan);
}
.tag-alert {
    background: #f97316;
}

/* BOTÕES */

.btn-primary,
.btn-secondary {
    border-radius: 999px;
    border: none;
    padding: 9px 16px;
    font-size: 14px;
    cursor: pointer;
    transition: transform var(--transition-fast), box-shadow var(--transition-fast), background var(--transition-fast);
    font-weight: 500;
}

.btn-primary {
    background: linear-gradient(135deg, var(--accent-blue), var(--accent-cyan));
    color: #ecfeff;
    box-shadow: 0 12px 35px rgba(37, 99, 235, 0.45);
}

.btn-primary:hover {
    transform: translateY(-1px);
    box-shadow: 0 18px 45px rgba(37, 99, 235, 0.6);
}

.btn-secondary {
    background: rgba(15, 23, 42, 0.9);
    color: var(--text-main);
    border: 1px solid rgba(148, 163, 184, 0.4);
}

.btn-secondary:hover {
    background: rgba(30, 64, 175, 0.35);
}

.full-width {
    width: 100%;
    margin-top: 10px;
}

/* FORMULÁRIO */

.form-row {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 12px;
    margin-bottom: 10px;
}

.form-field {
    display: flex;
    flex-direction: column;
    gap: 4px;
}

.form-field label {
    font-size: 13px;
    color: var(--text-muted);
}

.form-field input,
.form-field select {
    background: rgba(15, 23, 42, 0.85);
    border-radius: var(--radius-md);
    border: 1px solid rgba(148, 163, 184, 0.45);
    padding: 7px 10px;
    color: var(--text-main);
    font-size: 14px;
    outline: none;
    transition: border var(--transition-fast), box-shadow var(--transition-fast), background var(--transition-fast);
}

.form-field input::placeholder {
    color: #64748b;
}

.form-field input:focus,
.form-field select:focus {
    border-color: var(--accent-cyan);
    box-shadow: 0 0 0 1px rgba(56, 189, 248, 0.4);
    background: rgba(15, 23, 42, 1);
}

/* RESULTADO */

.result-card h3 {
    font-size: 18px;
    margin-bottom: 6px;
}

.result-summary {
    color: var(--text-muted);
    font-size: 14px;
    margin-bottom: 10px;
}

.recomendations-list {
    margin-left: 18px;
    color: var(--text-main);
    font-size: 14px;
    display: flex;
    flex-direction: column;
    gap: 4px;
}

.hidden {
    display: none;
}

/* FOOTER */

.footer {
    border-top: 1px solid var(--border-soft);
    padding: 14px 7vw 18px;
    text-align: center;
    color: var(--text-muted);
    font-size: 12px;
    background: radial-gradient(circle at top, #020617 0, #000 80%);
}

/* RESPONSIVO */

@media (max-width: 700px) {
    .topbar {
        flex-direction: column;
        align-items: flex-start;
        gap: 8px;
    }
    .nav {
        width: 100%;
        justify-content: flex-start;
        flex-wrap: wrap;
    }
    .section h1 {
        font-size: 26px;
    }
}
function abrirFormularioArea() {
    const form = document.getElementById("formSolo");
    if (form) {
        window.location.hash = "#analise";
        form.scrollIntoView({ behavior: "smooth" });
    }
}

function gerarRelatorioGeral() {
    alert(
        "Relatório geral (exemplo):\n\n" +
        "- 3 áreas cadastradas\n" +
        "- 18% de economia estimada em adubos\n" +
        "- Recomendado: aumentar matéria orgânica em 2 áreas."
    );
}

function analisarSolo(event) {
    event.preventDefault();

    const nomeArea = document.getElementById("nomeArea").value.trim() || "Área sem nome";
    const tamanhoArea = parseFloat(document.getElementById("tamanhoArea").value);
    const tipoSolo = document.getElementById("tipoSolo").value;
    const phSolo = parseFloat(document.getElementById("phSolo").value);
    const matOrganica = parseFloat(document.getElementById("matOrganica").value);
    const cultura = document.getElementById("cultura").value.trim() || "cultura não informada";
    const irrigacao = document.getElementById("irrigacao").value;

    const resultado = document.getElementById("resultadoAnalise");
    const resumoArea = document.getElementById("resumoArea");
    const listaRecomendacoes = document.getElementById("listaRecomendacoes");

    listaRecomendacoes.innerHTML = "";
    const recomendacoes = [];

    // Regras bem simples, só para exemplo:

    // pH
    if (!isNaN(phSolo)) {
        if (phSolo < 5.5) {
            recomendacoes.push(
                "O pH está baixo. Avalie a aplicação de calcário, de forma gradual, " +
                "para corrigir a acidez e melhorar a disponibilidade de nutrientes."
            );
        } else if (phSolo > 6.5) {
            recomendacoes.push(
                "O pH está mais alto que o ideal para muitas culturas. " +
                "Evite calagem excessiva e acompanhe novas análises de solo."
            );
        } else {
            recomendacoes.push(
                "O pH está em uma faixa boa para a maioria das culturas, " +
                "mantenha o manejo atual e faça nova análise periodicamente."
            );
        }
    } else {
        recomendacoes.push("Informe o pH do solo para receber recomendações mais precisas.");
    }

    // Matéria orgânica
    if (!isNaN(matOrganica)) {
        if (matOrganica < 2) {
            recomendacoes.push(
                "Matéria orgânica baixa. Considere usar palhada, adubos verdes e restos de cultura " +
                "para aumentar a vida do solo e reduzir dependência de fertilizantes químicos."
            );
        } else if (matOrganica >= 2 && matOrganica <= 4) {
            recomendacoes.push(
                "Matéria orgânica em nível razoável. Continue mantendo cobertura do solo " +
                "e rotação de culturas para não perder qualidade."
            );
        } else {
            recomendacoes.push(
                "Matéria orgânica alta. Ótimo! Mantenha práticas conservacionistas " +
                "para preservar essa vantagem produtiva."
            );
        }
    } else {
        recomendacoes.push("Informe o valor de matéria orgânica para recomendações de adubação orgânica.");
    }

    // Tipo de solo
    if (tipoSolo === "arenoso") {
        recomendacoes.push(
            "Solo arenoso: use adubação parcelada e irrigação mais frequente (se possível), " +
            "pois nutrientes e água se perdem mais rápido."
        );
    } else if (tipoSolo === "argiloso") {
        recomendacoes.push(
            "Solo argiloso: atenção à compactação. Evite tráfego pesado com o solo úmido " +
            "e use plantas de raiz profunda para melhorar a estrutura."
        );
    } else if (tipoSolo === "misturado") {
        recomendacoes.push(
            "Solo misturado: aproveite a boa retenção de água, mas mantenha rotação de culturas " +
            "para não esgotar nutrientes em áreas específicas."
        );
    } else {
        recomendacoes.push("Informe o tipo de solo para personalizar melhor o manejo.");
    }

    // Irrigação
    if (irrigacao === "sim") {
        recomendacoes.push(
            "Com irrigação, ajuste lâminas de água conforme a necessidade da cultura " +
            "para evitar desperdício e lixiviação de nutrientes."
        );
    } else if (irrigacao === "nao") {
        recomendacoes.push(
            "Sem irrigação: priorize cobertura do solo (palhada, plantio direto) " +
            "para conservar a umidade e reduzir riscos em períodos de seca."
        );
    }

    // Tamanho da área
    if (!isNaN(tamanhoArea) && tamanhoArea > 0) {
        if (tamanhoArea <= 5) {
            recomendacoes.push(
                "Área pequena: foque em práticas simples e baratas, como adubação orgânica local " +
                "e manejo cuidadoso de insumos."
            );
        } else {
            recomendacoes.push(
                "Área maior: pode valer a pena registrar cada talhão separadamente " +
                "para otimizar adubação e reduzir desperdícios."
            );
        }
    }

    // Resumo
    resumoArea.textContent =
        `${nomeArea} · ${!isNaN(tamanhoArea) ? tamanhoArea + " ha · " : ""}` +
        `${cultura} · ${tipoSolo || "tipo de solo não informado"}`;

    recomendacoes.forEach(texto => {
        const li = document.createElement("li");
        li.textContent = texto;
        listaRecomendacoes.appendChild(li);
    });

    resultado.classList.remove("hidden");
    resultado.scrollIntoView({ behavior: "smooth" });
}
# AgroSolo Consciente – Projeto Agrinho 2026

Aplicativo web com foco em **cuidado inteligente do solo** para pequenos e grandes produtores,
ajudando a **reduzir desperdício de insumos** e **aumentar o lucro com consciência ambiental**.

## Tecnologias

- HTML
- CSS (estilo minimalista tecnológico com azul, cyan e teal)
- JavaScript (regras simples de recomendação)

## Como rodar

1. Baixe ou clone este repositório.
2. Abra o arquivo `index.html` no navegador.
3. Preencha o formulário de análise do solo para ver as recomendações iniciais.

## Ideia principal

Usar dados simples da propriedade (tipo de solo, pH, matéria orgânica, cultura, irrigação)
para gerar uma **retroalimentação** de manejo sustentável:

- Menos desperdício de matéria-prima
- Melhor uso de fertilizantes e água
- Manutenção da produtividade com mais respeito ao solo
