<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ORDO REALITAS · Procurados</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0a0a0a;
            color: #d0d0d0;
            font-family: 'Courier New', monospace;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        /* Barra superior estilo governamental */
        .top-bar {
            width: 100%;
            background: #000;
            border-bottom: 2px solid #8b0000;
            padding: 10px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.9rem;
            letter-spacing: 1px;
        }

        .gov-info {
            display: flex;
            gap: 30px;
            align-items: center;
        }

        .gov-info span {
            color: #999;
            font-size: 0.8rem;
        }

        .accessibility {
            display: flex;
            gap: 15px;
            font-size: 0.75rem;
            color: #666;
        }

        /* Cabeçalho principal */
        .header {
            width: 100%;
            max-width: 1200px;
            padding: 30px 20px;
            text-align: center;
            border-bottom: 3px solid #8b0000;
            margin-bottom: 20px;
        }

        .logo-container {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
            margin-bottom: 10px;
        }

        .logo {
            width: 80px;
            height: 80px;
            background: #000;
            border: 2px solid #8b0000;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.5rem;
            color: #8b0000;
        }

        .org-name {
            font-size: 2rem;
            font-weight: bold;
            letter-spacing: 3px;
            color: #fff;
        }

        .subtitle {
            color: #8b0000;
            font-size: 1.2rem;
            letter-spacing: 2px;
            margin-top: 5px;
        }

        /* Container principal */
        .container {
            max-width: 1200px;
            width: 100%;
            padding: 20px;
        }

        /* Aviso de confidencialidade */
        .classified-notice {
            background: #000;
            border: 2px solid #8b0000;
            padding: 20px;
            text-align: center;
            margin-bottom: 30px;
            font-size: 1.1rem;
            letter-spacing: 1px;
            color: #8b0000;
            font-weight: bold;
        }

        /* Grid de procurados */
        .wanted-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .wanted-card {
            background: #0d0d0d;
            border: 1px solid #333;
            padding: 20px;
            position: relative;
            transition: 0.3s;
        }

        .wanted-card:hover {
            border-color: #8b0000;
            box-shadow: 0 0 20px rgba(139, 0, 0, 0.3);
        }

        .danger-level {
            position: absolute;
            top: 10px;
            right: 10px;
            background: #8b0000;
            color: #fff;
            padding: 3px 12px;
            font-size: 0.75rem;
            letter-spacing: 2px;
            font-weight: bold;
        }

        .wanted-photo {
            width: 100%;
            height: 250px;
            background: #1a1a1a;
            border: 1px solid #333;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #666;
            font-size: 0.9rem;
            overflow: hidden;
        }

        .wanted-photo img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            filter: grayscale(100%);
        }

        .wanted-name {
            font-size: 1.3rem;
            font-weight: bold;
            color: #fff;
            margin-bottom: 5px;
        }

        .wanted-alias {
            color: #8b0000;
            font-size: 0.9rem;
            margin-bottom: 10px;
        }

        .wanted-info {
            font-size: 0.85rem;
            line-height: 1.5;
            color: #ccc;
            margin-bottom: 15px;
        }

        .wanted-footer {
            border-top: 1px solid #333;
            padding-top: 10px;
            font-size: 0.75rem;
            color: #666;
            display: flex;
            justify-content: space-between;
        }

        /* Botões de ação */
        .action-buttons {
            display: flex;
            gap: 10px;
            margin: 20px 0;
            flex-wrap: wrap;
        }

        .btn {
            background: #000;
            border: 2px solid #888;
            color: #fff;
            padding: 10px 20px;
            font-family: 'Courier New', monospace;
            letter-spacing: 2px;
            cursor: pointer;
            transition: 0.3s;
            text-transform: uppercase;
            font-size: 0.9rem;
        }

        .btn:hover {
            border-color: #8b0000;
            background: #1a0000;
        }

        .btn-danger {
            border-color: #8b0000;
            color: #ff0000;
        }

        .btn-danger:hover {
            background: #8b0000;
            color: #fff;
        }

        /* Formulário de adição */
        .add-form {
            background: #0a0a0a;
            border: 1px solid #333;
            padding: 20px;
            margin: 20px 0;
            display: none;
        }

        .add-form.show {
            display: block;
        }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            color: #888;
            margin-bottom: 5px;
            letter-spacing: 1px;
            font-size: 0.9rem;
        }

        input, textarea, select {
            width: 100%;
            background: #111;
            border: 1px solid #333;
            color: #fff;
            padding: 10px;
            font-family: 'Courier New', monospace;
        }

        input:focus, textarea:focus, select:focus {
            outline: none;
            border-color: #8b0000;
        }

        /* Rodapé */
        .footer {
            width: 100%;
            background: #000;
            border-top: 2px solid #8b0000;
            padding: 20px;
            text-align: center;
            margin-top: 40px;
            color: #666;
            font-size: 0.8rem;
            letter-spacing: 1px;
        }

        .watermark {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) rotate(-15deg);
            font-size: 5rem;
            color: rgba(139, 0, 0, 0.05);
            pointer-events: none;
            z-index: -1;
            white-space: nowrap;
            letter-spacing: 10px;
        }

        @media (max-width: 768px) {
            .wanted-grid {
                grid-template-columns: 1fr;
            }
            .header {
                padding: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="top-bar">
        <div class="gov-info">
            <span>███ ORDO REALITAS ███</span>
            <span>|</span>
            <span>ACESSO RESTRITO</span>
            <span>|</span>
            <span>NÍVEL SIGMA</span>
        </div>
        <div class="accessibility">
            <span>🔍</span>
            <span>⚙️</span>
            <span>📡</span>
        </div>
    </div>

    <div class="header">
        <div class="logo-container">
            <div class="logo">⟡</div>
            <div>
                <div class="org-name">ORDO REALITAS</div>
                <div class="subtitle">DIVISÃO DE CONTENÇÃO E CAPTURA</div>
            </div>
        </div>
    </div>

    <div class="watermark">CONFIDENCIAL</div>

    <div class="container">
        <div class="classified-notice">
            ⚠ ESTAS PESSOAS ESTÃO SENDO PROCURADAS POR REPRESENTAREM UM PERIGO IMINENTE À MEMBRANA E À SOCIEDADE ⚠
        </div>

        <div class="action-buttons">
            <button class="btn" onclick="toggleForm()">📋 ADICIONAR PROCURADO</button>
            <button class="btn btn-danger" onclick="exportarLista()">🖨️ EXPORTAR RELATÓRIO</button>
        </div>

        <div class="add-form" id="addForm">
            <h3 style="color:#8b0000;margin-bottom:15px;">NOVO REGISTRO DE PROCURADO</h3>
            <div class="form-group">
                <label>Foto (URL)</label>
                <input type="text" id="fotoUrl" placeholder="https://...">
            </div>
            <div class="form-group">
                <label>Nome Completo</label>
                <input type="text" id="nomeProcurado" placeholder="NOME COMPLETO">
            </div>
            <div class="form-group">
                <label>Codinome/Apelido</label>
                <input type="text" id="codinome" placeholder="Codename">
            </div>
            <div class="form-group">
                <label>Nível de Periculosidade</label>
                <select id="nivelPerigo">
                    <option value="ALTO">ALTO</option>
                    <option value="EXTREMO">EXTREMO</option>
                    <option value="CRÍTICO">CRÍTICO</option>
                </select>
            </div>
            <div class="form-group">
                <label>Descrição/Crimes</label>
                <textarea id="descricao" rows="4"></textarea>
            </div>
            <div class="form-group">
                <label>Última Localização</label>
                <input type="text" id="localizacao" placeholder="Cidade, Estado">
            </div>
            <button class="btn" onclick="adicionarProcurado()">ADICIONAR</button>
        </div>

        <div class="wanted-grid" id="wantedGrid">
            <!-- Gerado dinamicamente -->
        </div>
    </div>

    <div class="footer">
        ORDO REALITAS © 20██ | TODOS OS DIREITOS RESERVADOS | ACESSO MONITORADO
    </div>

<script>
// Banco de dados inicial de procurados (exemplos)
let procurados = [
    {
        foto: '',
        nome: 'SILVA, ALEXANDRE',
        codinome: 'O Cultista',
        nivel: 'EXTREMO',
        descricao: 'Ex-agente da Ordem. Traidor. Realizou rituais proibidos de invocação do Outro Lado. Extremamente perigoso e conhecedor dos protocolos internos.',
        localizacao: 'São Paulo, SP'
    },
    {
        foto: '',
        nome: 'FERRAZ, BEATRIZ',
        codinome: 'A Quebrada',
        nivel: 'CRÍTICO',
        descricao: 'Ocultista de alto nível. Responsável pelo rompimento da Membrana em Minas Gerais. Pode manipular a realidade ao seu redor.',
        localizacao: 'Ouro Preto, MG'
    },
    {
        foto: '',
        nome: 'ROCHA, CAIO',
        codinome: 'O Exterminador',
        nivel: 'ALTO',
        descricao: 'Combatente renegado. Utiliza técnicas proibidas de combate paranormal. Armado e extremamente treinado em artes marciais ocultas.',
        localizacao: 'Rio de Janeiro, RJ'
    }
];

function renderizarProcurados() {
    const grid = document.getElementById('wantedGrid');
    grid.innerHTML = procurados.map((p, index) => `
        <div class="wanted-card">
            <div class="danger-level">${p.nivel}</div>
            <div class="wanted-photo">
                ${p.foto ? `<img src="${p.foto}" alt="${p.nome}">` : 'SEM FOTO DISPONÍVEL'}
            </div>
            <div class="wanted-name">${p.nome}</div>
            <div class="wanted-alias">"${p.codinome}"</div>
            <div class="wanted-info">${p.descricao}</div>
            <div class="wanted-footer">
                <span>📍 ${p.localizacao}</span>
                <span>📋 REF: ${String(index + 1).padStart(3, '0')}</span>
            </div>
            <button class="btn" onclick="removerProcurado(${index})" style="margin-top:10px;width:100%;font-size:0.75rem;">REMOVER</button>
        </div>
    `).join('');
}

function adicionarProcurado() {
    const foto = document.getElementById('fotoUrl').value;
    const nome = document.getElementById('nomeProcurado').value.toUpperCase();
    const codinome = document.getElementById('codinome').value;
    const nivel = document.getElementById('nivelPerigo').value;
    const descricao = document.getElementById('descricao').value;
    const localizacao = document.getElementById('localizacao').value;
    
    if (!nome) return alert('Nome é obrigatório!');
    
    procurados.push({ foto, nome, codinome, nivel, descricao, localizacao });
    renderizarProcurados();
    
    // Limpa o formulário
    document.querySelectorAll('#addForm input, #addForm textarea').forEach(el => el.value = '');
    document.getElementById('addForm').classList.remove('show');
}

function removerProcurado(index) {
    procurados.splice(index, 1);
    renderizarProcurados();
}

function toggleForm() {
    document.getElementById('addForm').classList.toggle('show');
}

function exportarLista() {
    let relatorio = 'ORDO REALITAS - RELATÓRIO DE PROCURADOS\n';
    relatorio += '='.repeat(60) + '\n\n';
    procurados.forEach((p, i) => {
        relatorio += `REF: ${String(i + 1).padStart(3, '0')}\n`;
        relatorio += `NOME: ${p.nome}\n`;
        relatorio += `CODENOME: ${p.codinome}\n`;
        relatorio += `NÍVEL: ${p.nivel}\n`;
        relatorio += `LOCALIZAÇÃO: ${p.localizacao}\n`;
        relatorio += `OBSERVAÇÕES: ${p.descricao}\n`;
        relatorio += '-'.repeat(40) + '\n\n';
    });
    alert('RELATÓRIO EXPORTADO!\n\n' + relatorio + '\n(Na versão desktop, você pode copiar este texto)');
}

window.onload = renderizarProcurados;
</script>
</body>
</html>
