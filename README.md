<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Lusther 3D - Plataforma</title>
    <style>

/* Esconde o cabeçalho automático do GitHub Pages */
body > header, .ui-header, h1:first-of-type {
    display: none !important;
}

/* Se o texto "Multiversy" estiver vindo de um <h1> que o GitHub injeta: */
header h1 { display: none; }

#multiversy {
    position: relative; /* Essencial para prender a legenda aqui dentro */
    width: 100%;
    height: 600px; /* Ou a altura que você desejar */
    background: #000;
    overflow: hidden;
}

        body {
            background: linear-gradient(45deg, #4f4f4f, #ffd700, #000000, #ffffff, #c0c0c0, #ff8c00);
            background-size: 400% 400%;
            background-attachment: fixed;
            color: white;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            animation: BackgroundGradient 10s ease infinite;
        }

        @keyframes BackgroundGradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        nav {
            background: rgba(0, 0, 0, 0.8);
            padding: 15px;
            position: sticky;
            top: 0;
            z-index: 1000;
            text-align: center;
            backdrop-filter: blur(10px);
            border-bottom: 2px solid gold;
            display: none;
            overflow-x: auto;
            white-space: nowrap;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin: 0 10px;
            font-weight: bold;
            text-transform: uppercase;
            transition: 0.3s;
            cursor: pointer;
            font-size: 11px;
        }

        nav a:hover { color: gold; }

        .secao { display: none; padding: 20px; min-height: 80vh; }
        .ativa { display: block; animation: fadeIn 0.5s; }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        .header-perfil { text-align: center; padding: 40px 20px; background: rgba(0, 0, 0, 0.4); border-radius: 15px; margin-top: 20px; max-width: 800px; margin-left: auto; margin-right: auto; }
        
        input, textarea, select {
            width: 90%;
            padding: 12px;
            margin: 8px 0;
            border-radius: 8px;
            border: 1px solid #ccc;
            outline: none;
            background: white;
        }

        button { background: #790fcf; color: white; border: none; padding: 12px; border-radius: 5px; cursor: pointer; width: 100%; font-weight: bold; transition: 0.3s; }
        button:hover { filter: brightness(1.2); }

        .foto-perfil {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid gold;
            background: #222;
        }

        .stats { display: flex; justify-content: center; gap: 30px; margin: 15px 0; }

        .galeria-fotos {
            display: flex;
            flex-direction: column;
            gap: 25px;
            margin-top: 30px;
            text-align: left;
        }

        .post-card {
            background: rgba(0, 0, 0, 0.7);
            border-radius: 12px;
            padding: 15px;
            border: 1px solid rgba(255, 215, 0, 0.3);
            max-width: 500px;
            margin: 0 auto;
            width: 100%;
        }

        .post-card img { width: 100%; border-radius: 8px; margin-bottom: 10px; }
        .post-info p { margin: 5px 0; }
        .post-tags { color: #ffd700; font-size: 0.8em; font-weight: bold; }
        .post-categoria { display: inline-block; background: gold; color: black; padding: 2px 8px; border-radius: 4px; font-size: 0.7em; text-transform: uppercase; margin-bottom: 5px; }
        
        .btn-group { display: flex; gap: 10px; margin-top: 10px; }
        .btn-interagir { width: auto; padding: 6px 12px; font-size: 0.8em; }

        .comentarios-area {
            margin-top: 10px;
            border-top: 1px solid #444;
            padding-top: 10px;
            font-size: 0.85em;
        }
        
        .comentario-item { margin-bottom: 4px; border-bottom: 1px solid #333; padding: 2px 0; }
        
        .btn-perigo { background: #ff4757; margin-top: 20px; font-size: 0.8em; width: auto; padding: 8px 15px; }
        
        .info-card { background: rgba(255, 215, 0, 0.1); border: 1px solid gold; padding: 20px; border-radius: 10px; margin-top: 20px; }

        .btn-chat-flutuante {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: gold;
            color: black;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: none;
            align-items: center;
            justify-content: center;
            font-size: 28px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0,0,0,0.5);
            z-index: 2000;
            border: 2px solid #000;
            transition: 0.3s;
        }
        
        .btn-chat-flutuante:hover { transform: scale(1.1); background: white; }

        .chat-container {
            display: flex;
            height: 60vh;
            background: rgba(0, 0, 0, 0.8);
            border: 1px solid gold;
            border-radius: 12px;
            overflow: hidden;
            margin-top: 20px;
        }

        .lista-contatos {
            width: 30%;
            border-right: 1px solid #444;
            overflow-y: auto;
            text-align: left;
            background: rgba(255,255,255,0.05);
        }

        .contato-item {
            padding: 12px;
            border-bottom: 1px solid #222;
            cursor: pointer;
        }
        
        .contato-item:hover { background: rgba(255, 215, 0, 0.2); }

        .janela-conversa {
            width: 70%;
            display: flex;
            flex-direction: column;
            background: rgba(0,0,0,0.5);
        }

        #mensagens-corpo {
            flex-grow: 1;
            padding: 15px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 10px;
            text-align: left;
        }

        .msg-balao {
            padding: 10px 15px;
            border-radius: 15px;
            max-width: 80%;
            font-size: 0.9em;
            word-wrap: break-word;
        }
        .msg-enviada { align-self: flex-end; background: #790fcf; color: white; }
        .msg-recebida { align-self: flex-start; background: #333; color: white; border: 1px solid #555; }

        .container-grafico {
            width: 100%;
            height: 600px;
            border-radius: 12px;
            overflow: hidden;
            border: 2px solid gold;
            margin-top: 15px;
            background: #000;
        }
    </style>
</head>

<body>

    <nav id="menu-principal">
        <a onclick="mostrar('home')">🏠 Mural</a>
        <a onclick="mostrar('multiversy')">🌌 Multiversy</a>
        <a onclick="mostrar('exchange')">💱 Exchange</a>
        <a onclick="mostrar('quadrinhos')">📚 Quadrinhos</a>
        <a onclick="mostrar('livros')">📖 Livros</a>
        <a onclick="mostrar('impressao')">⚙️ Impressão 3D</a>
        <a onclick="mostrar('perfil')">👤 Perfil</a>
        <a onclick="logout()" style="color: #ff4757;">🚪 Sair</a>
    </nav>

    <button id="btn-chat" class="btn-chat-flutuante" onclick="mostrar('chat')">💬</button>

    <div id="login" class="secao ativa">
        <div class="header-perfil" style="max-width: 400px; margin: 60px auto;">
            <div id="area-login">
                <h2>🔑 Acessar Plataforma</h2>
                <input type="email" id="login-email" placeholder="E-mail">
                <input type="password" id="login-senha" placeholder="Senha">
                <button onclick="realizarLogin()">ENTRAR</button>
                <p>Não tem conta? <a onclick="alternarTela('cadastro')" style="color: gold; cursor: pointer;">Cadastre-se</a></p>
            </div>
            <div id="area-cadastro" style="display: none;">
                <h2>📝 Criar Conta</h2>
                <input type="text" id="cad-nome" placeholder="Nome Completo">
                <input type="email" id="cad-email" placeholder="E-mail">
                <input type="password" id="cad-senha" placeholder="Senha">
                <button onclick="cadastrarUsuario()" style="background: #2ecc71;">FINALIZAR CADASTRO</button>
                <p><a onclick="alternarTela('login')" style="color: gold;">Voltar</a></p>
            </div>
        </div>
    </div>

    <div id="chat" class="secao">
        <div class="header-perfil" style="max-width: 1000px;">
            <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:10px">
                <h2>💬 Mensagens</h2>
                <button onclick="abrirModalGrupo()" style="width:auto; padding:5px 15px; background:gold; color:black">+ NOVO GRUPO</button>
            </div>
            <div class="chat-container">
                <div class="lista-contatos" id="chat-usuarios"></div>
                <div class="janela-conversa">
                    <div id="chat-status" style="padding: 10px; background: rgba(0,0,0,0.3); border-bottom: 1px solid gold; font-size: 0.8em; display:flex; justify-content:space-between">
                        <span id="txt-status">Selecione uma conversa (Somente amigos mútuos)</span>
                        <div id="acoes-chat" style="display:none">
                            <button id="btn-del-gp" onclick="deletarGrupo()" style="background:red; width:auto; padding:2px 8px; font-size:10px; display:none">EXCLUIR GRUPO</button>
                            <button onclick="bloquearContato()" style="background:#444; width:auto; padding:2px 8px; font-size:10px">BLOQUEAR</button>
                        </div>
                    </div>
                    <div id="mensagens-corpo"></div>
                    <div id="chat-controles" style="display:none; padding: 10px; background: rgba(0,0,0,0.4);">
                        <div style="display: flex; gap: 10px;">
                            <input type="text" id="msg-input" placeholder="Sua mensagem..." style="margin:0;">
                            <button onclick="enviarMensagem()" style="width: 80px;">Enviar</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div id="modal-grupo" style="display:none; position:fixed; top:50%; left:50%; transform:translate(-50%,-50%); background:#1a1a1a; padding:20px; border:2px solid gold; border-radius:10px; z-index:3000; width:300px; text-align:center">
        <h3>Novo Grupo</h3>
        <input type="text" id="nome-grupo-novo" placeholder="Nome do Grupo">
        <div id="lista-membros-gp" style="text-align:left; max-height:150px; overflow-y:auto; margin:10px 0; font-size:12px"></div>
        <button onclick="confirmarGrupo()">CRIAR</button>
        <button onclick="toggleElement('modal-grupo')" style="background:#444; margin-top:5px">CANCELAR</button>
    </div>

    <div id="multiversy" class="secao">
        <div class="header-perfil">
            <h2>🌌 Multiversy 3D</h2>
            <div class="info-card" style="text-align: center; padding: 40px;">
                <p>Clique abaixo para entrar na experiência interativa do Multiverso.</p>
                <button onclick="abrirJanelaMultiverso()" style="background: gold; color: black; width: auto; padding: 15px 30px; margin-top: 20px; font-size: 16px;">
                    INICIAR UNIVERSO 3D
                </button>
            </div>
        </div>
    </div>

    <div id="exchange" class="secao">
        <div class="header-perfil" style="max-width: 95%; width: 1100px;">
            <h2>💱 Exchange Lusther 3D</h2>
            <div class="container-grafico">
                <iframe width="100%" height="100%" src="https://www.geckoterminal.com/es/polygon_pos/pools/0x0de9bb162ce01f953647c236fff94a9ed492c341?embed=1&info=0&swaps=1" frameborder="0"></iframe>
            </div>
        </div>
    </div>

    <div id="home" class="secao"><div class="header-perfil"><h1>Mural da Comunidade</h1><div id="feed-global" class="galeria-fotos"></div></div></div>
    <div id="quadrinhos" class="secao"><div class="header-perfil"><h2>📚 Quadrinhos</h2><div id="feed-quadrinhos" class="galeria-fotos"></div></div></div>

    <div id="livros" class="secao">
        <div class="header-perfil" style="max-width: 900px; padding: 0; overflow: hidden; border: 2px solid gold;">
            <div style="background-color: #f2e8d5; background-image: url('https://www.transparenttextures.com/patterns/paper-fibers.png'); color: #3b352a; font-family: 'Georgia', serif; padding: 30px; text-align: left;">
                <div style="background: rgba(255, 255, 255, 0.3); padding: 25px; border-radius: 8px; border: 1px solid #c9bca3; margin-bottom: 40px;">
                    <button onclick="salvarObra()" style="background: #5d5444; color: white; border-radius: 0; font-family: 'Georgia', serif;">Biblioteca Fechada</button>
                </div>
            </div>
        </div>
    </div>

    <div id="impressao" class="secao"><div class="header-perfil"><h2>⚙️ Impressão 3D</h2><div id="feed-impressao" class="galeria-fotos"></div></div></div>

    <div id="perfil" class="secao">
        <div class="header-perfil">
            <img id="display-foto" src="https://via.placeholder.com/150" class="foto-perfil">
            <h2 id="display-nome">...</h2>
            <p id="display-bio">...</p>
            <div class="stats">
                <div><span id="num-seguidores">0</span><br>Seguidores</div>
                <div><span id="num-seguindo">0</span><br>Seguindo</div>
            </div>
            <div style="display: flex; gap: 10px; justify-content: center;">
                <button onclick="toggleElement('edit-perfil')" style="width: auto; background: #555;">⚙️ Editar</button>
                <button onclick="toggleElement('postar-foto')" style="width: auto; background: gold; color: black;">📸 Postar</button>
            </div>
            
            <div id="edit-perfil" style="display:none; margin-top:20px;"><input type="file" id="input-foto"><textarea id="input-bio"></textarea><button onclick="salvarPerfil()">Salvar</button></div>
            <div id="postar-foto" style="display:none; margin-top:20px;">
                <select id="post-cat"><option value="mural">Mural</option><option value="quadrinhos">Quadrinhos</option><option value="livros">Livros</option><option value="impressao">Impressão 3D</option></select>
                <input type="file" id="input-post"><input type="text" id="post-desc" placeholder="Descrição"><button onclick="postarFoto()">Publicar</button>
            </div>
            <div class="galeria-fotos" id="minha-galeria"></div>
            <button onclick="deletarConta()" class="btn-perigo">🗑️ Excluir Conta</button>
        </div>
    </div>

    <script>
        let logado = false;
        let usuarioAtual = null;
        let contatoAtivo = null;
        let chatTipo = '';

        window.onload = () => {
            const salvo = localStorage.getItem('sessao_ativa');
            if (salvo) {
                const conta = JSON.parse(localStorage.getItem(salvo));
                if (conta) loginSucesso(conta);
            }
        };

        function mostrar(idSecao) {
            if (!logado && idSecao !== 'login') return;
            document.querySelectorAll('.secao').forEach(s => s.classList.remove('ativa'));
            document.getElementById(idSecao).classList.add('ativa');
            
            if(idSecao === 'perfil') carregarPerfil();
            if(idSecao === 'home') carregarFeed('feed-global', 'todas');
            if(idSecao === 'chat') carregarListaChat();
            
            if(['quadrinhos','livros','impressao'].includes(idSecao)) carregarFeed('feed-'+idSecao, idSecao);
        }

        function alternarTela(t) { 
            document.getElementById('area-login').style.display = t === 'login' ? 'block' : 'none';
            document.getElementById('area-cadastro').style.display = t === 'cadastro' ? 'block' : 'none';
        }

        function cadastrarUsuario() {
            const n = document.getElementById('cad-nome').value, e = document.getElementById('cad-email').value, s = document.getElementById('cad-senha').value;
            if(!n || !e || !s) return alert("Preencha tudo!");
            if(localStorage.getItem(e)) return alert("Já existe!");
            localStorage.setItem(e, JSON.stringify({ nome: n, email: e, senha: s, bio: "", foto: "", posts: [], seguidores: 0, seguindo: 0, seguindo_lista: [], bloqueados: [] }));
            alert("Sucesso!"); alternarTela('login');
        }

        function realizarLogin() {
            const e = document.getElementById('login-email').value, s = document.getElementById('login-senha').value, c = JSON.parse(localStorage.getItem(e));
            if(c && c.senha === s) { localStorage.setItem('sessao_ativa', e); loginSucesso(c); } else alert("Erro!");
        }

        function loginSucesso(c) { 
            logado = true; 
            usuarioAtual = c.email; 
            document.getElementById('menu-principal').style.display = 'block'; 
            document.getElementById('btn-chat').style.display = 'flex';
            mostrar('home'); 
        }

        function logout() { localStorage.removeItem('sessao_ativa'); location.reload(); }

        function seguir(email) {
            if(email === usuarioAtual) return;
            // Melhoria: Fallback para evitar erro se o usuário não for encontrado
            let a = JSON.parse(localStorage.getItem(email)) || {};
            let eu = JSON.parse(localStorage.getItem(usuarioAtual)) || {};
            if(!eu.seguindo_lista) eu.seguindo_lista = [];
            
            if(!eu.seguindo_lista.includes(email)) {
                eu.seguindo_lista.push(email); eu.seguindo++; a.seguidores++;
            } else {
                eu.seguindo_lista = eu.seguindo_lista.filter(e => e !== email); eu.seguindo--; a.seguidores--;
            }
            localStorage.setItem(email, JSON.stringify(a)); 
            localStorage.setItem(usuarioAtual, JSON.stringify(eu));
            
            const secaoAtiva = document.querySelector('.secao.ativa').id;
            mostrar(secaoAtiva);
        }

        function carregarListaChat() {
            const lista = document.getElementById('chat-usuarios');
            lista.innerHTML = "";
            let eu = JSON.parse(localStorage.getItem(usuarioAtual)) || { seguindo_lista: [], bloqueados: [] };

            for (let i = 0; i < localStorage.length; i++) {
                const k = localStorage.key(i);
                if (k.startsWith('gp_')) {
                    const gp = JSON.parse(localStorage.getItem(k));
                    if (gp && gp.membros && gp.membros.includes(usuarioAtual)) {
                        const d = document.createElement('div');
                        d.className = 'contato-item';
                        d.innerHTML = `<span style="color:gold; font-size:10px">GRUPO</span><br><strong>${gp.nome}</strong>`;
                        d.onclick = () => abrirConversa(k, 'grupo');
                        lista.appendChild(d);
                    }
                }
            }

            for (let i = 0; i < localStorage.length; i++) {
                const k = localStorage.key(i);
                if (k === 'sessao_ativa' || !k.includes('@') || k === usuarioAtual || k.startsWith('gp_') || k.includes('_chat_')) continue;
                
                const alvo = JSON.parse(localStorage.getItem(k)) || {};
                const euSigo = eu.seguindo_lista && eu.seguindo_lista.includes(k);
                const eleMeSegue = alvo.seguindo_lista && alvo.seguindo_lista.includes(usuarioAtual);
                const bloqueado = (eu.bloqueados && eu.bloqueados.includes(k)) || (alvo.bloqueados && alvo.bloqueados.includes(usuarioAtual));

                if (euSigo && eleMeSegue && !bloqueado) {
                    const d = document.createElement('div');
                    d.className = 'contato-item';
                    d.innerHTML = `<strong>${alvo.nome}</strong><br><small style="color:gold">Amigo</small>`;
                    d.onclick = () => abrirConversa(k, 'privado');
                    lista.appendChild(d);
                }
            }
        }

        function abrirConversa(id, tipo) {
            contatoAtivo = id;
            chatTipo = tipo;
            const dados = JSON.parse(localStorage.getItem(id)) || { nome: "Usuário" };
            document.getElementById('txt-status').innerText = tipo === 'grupo' ? dados.nome : dados.nome;
            document.getElementById('chat-controles').style.display = 'block';
            document.getElementById('acoes-chat').style.display = 'flex';
            document.getElementById('btn-del-gp').style.display = (tipo === 'grupo' && dados.admin === usuarioAtual) ? 'block' : 'none';
            renderizarMensagens();
        }

        function enviarMensagem() {
            const texto = document.getElementById('msg-input').value;
            if(!texto || !contatoAtivo) return;
            const eu = JSON.parse(localStorage.getItem(usuarioAtual)) || { nome: "Eu" };
            const msg = { r: usuarioAtual, n: eu.nome, t: texto, id: Date.now() };

            if(chatTipo === 'grupo') {
                let gp = JSON.parse(localStorage.getItem(contatoAtivo));
                gp.mensagens.push(msg);
                localStorage.setItem(contatoAtivo, JSON.stringify(gp));
            } else {
                const chatKey = [usuarioAtual, contatoAtivo].sort().join('_chat_');
                let historico = JSON.parse(localStorage.getItem(chatKey)) || [];
                historico.push(msg);
                localStorage.setItem(chatKey, JSON.stringify(historico));
            }
            document.getElementById('msg-input').value = "";
            renderizarMensagens();
        }

        function renderizarMensagens() {
            const corpo = document.getElementById('mensagens-corpo');
            corpo.innerHTML = "";
            let historico = [];
            if(chatTipo === 'grupo') {
                const gpData = JSON.parse(localStorage.getItem(contatoAtivo));
                historico = gpData ? gpData.mensagens : [];
            } else {
                const chatKey = [usuarioAtual, contatoAtivo].sort().join('_chat_');
                historico = JSON.parse(localStorage.getItem(chatKey)) || [];
            }

            historico.forEach(m => {
                const div = document.createElement('div');
                div.className = `msg-balao ${m.r === usuarioAtual ? 'msg-enviada' : 'msg-recebida'}`;
                div.title = "Clique para apagar";
                div.onclick = () => apagarMensagem(m.id);
                const autor = (chatTipo === 'grupo' && m.r !== usuarioAtual) ? `<small style="color:gold;display:block">${m.n}</small>` : '';
                div.innerHTML = autor + m.t;
                corpo.appendChild(div);
            });
            // Melhoria: Scroll suave para a última mensagem
            corpo.scrollTo({ top: corpo.scrollHeight, behavior: 'smooth' });
        }

        function apagarMensagem(msgId) {
            if(!confirm("Apagar esta mensagem?")) return;
            if(chatTipo === 'grupo') {
                let gp = JSON.parse(localStorage.getItem(contatoAtivo));
                gp.mensagens = gp.mensagens.filter(m => m.id !== msgId);
                localStorage.setItem(contatoAtivo, JSON.stringify(gp));
            } else {
                const chatKey = [usuarioAtual, contatoAtivo].sort().join('_chat_');
                let hist = JSON.parse(localStorage.getItem(chatKey)) || [];
                localStorage.setItem(chatKey, JSON.stringify(hist.filter(m => m.id !== msgId)));
            }
            renderizarMensagens();
        }

        function abrirModalGrupo() {
            toggleElement('modal-grupo');
            const lista = document.getElementById('lista-membros-gp');
            lista.innerHTML = "";
            let eu = JSON.parse(localStorage.getItem(usuarioAtual)) || { seguindo_lista: [] };
            for (let i = 0; i < localStorage.length; i++) {
                const k = localStorage.key(i);
                if (k.includes('@') && k !== usuarioAtual && !k.startsWith('gp_')) {
                    const alvo = JSON.parse(localStorage.getItem(k)) || {};
                    if(eu.seguindo_lista && eu.seguindo_lista.includes(k) && alvo.seguindo_lista && alvo.seguindo_lista.includes(usuarioAtual)) {
                        lista.innerHTML += `<label><input type="checkbox" class="check-membro" value="${k}"> ${alvo.nome}</label><br>`;
                    }
                }
            }
        }

        function confirmarGrupo() {
            const nome = document.getElementById('nome-grupo-novo').value;
            const selecionados = Array.from(document.querySelectorAll('.check-membro:checked')).map(cb => cb.value);
            if(!nome || selecionados.length === 0) return alert("Erro nos dados!");
            const idGp = 'gp_' + Date.now();
            localStorage.setItem(idGp, JSON.stringify({ nome: nome, admin: usuarioAtual, membros: [usuarioAtual, ...selecionados], mensagens: [] }));
            toggleElement('modal-grupo'); carregarListaChat();
        }

        function deletarGrupo() {
            if(confirm("Excluir grupo?")) { localStorage.removeItem(contatoAtivo); contatoAtivo = null; carregarListaChat(); }
        }

        function bloquearContato() {
            if(confirm("Bloquear contato?")) {
                let eu = JSON.parse(localStorage.getItem(usuarioAtual)) || {};
                if(!eu.bloqueados) eu.bloqueados = [];
                eu.bloqueados.push(contatoAtivo);
                localStorage.setItem(usuarioAtual, JSON.stringify(eu));
                contatoAtivo = null; carregarListaChat();
            }
        }

        function carregarFeed(containerId, catFiltro) {
            const f = document.getElementById(containerId); if(!f) return; f.innerHTML = ""; let posts = [];
            for (let i = 0; i < localStorage.length; i++) {
                const k = localStorage.key(i); if (k === 'sessao_ativa' || !k.includes('@') || k.includes('_chat_') || k.startsWith('gp_')) continue;
                const c = JSON.parse(localStorage.getItem(k)) || { posts: [] };
                if (c.posts) c.posts.forEach(p => { if(catFiltro === 'todas' || p.categoria === catFiltro) posts.push({ ...p, autorNome: c.nome, autorEmail: c.email }); });
            }
            posts.sort((a, b) => b.id - a.id).forEach(p => f.appendChild(criarCardPost(p, p.autorEmail === usuarioAtual)));
        }

        function carregarPerfil() {
            const c = JSON.parse(localStorage.getItem(usuarioAtual)) || { nome: "Usuário", posts: [] };
            document.getElementById('display-nome').innerText = c.nome;
            document.getElementById('display-bio').innerText = c.bio || "Sem bio.";
            document.getElementById('display-foto').src = c.foto || "https://via.placeholder.com/150";
            document.getElementById('num-seguidores').innerText = c.seguidores || 0;
            document.getElementById('num-seguindo').innerText = c.seguindo || 0;
            const g = document.getElementById('minha-galeria'); g.innerHTML = "";
            if(c.posts) c.posts.forEach(p => g.appendChild(criarCardPost({...p, autorNome: c.nome, autorEmail: c.email}, true)));
        }

        function criarCardPost(p, eMeu) {
            const eu = JSON.parse(localStorage.getItem(usuarioAtual)) || { seguindo_lista: [] };
            const jaSigo = eu.seguindo_lista && eu.seguindo_lista.includes(p.autorEmail);

            const d = document.createElement('div'); d.className = 'post-card';
            d.innerHTML = `<span class="post-categoria">${p.categoria}</span><img src="${p.imagem}"><div class="post-info">
                <p><strong>${p.autorNome}</strong> ${p.descricao}</p>
                <div class="btn-group">
                    <button class="btn-interagir" onclick="interagir('${p.autorEmail}', ${p.id}, 'like')">❤️ ${p.likes}</button>
                    ${!eMeu ? `<button class="btn-interagir" style="background:${jaSigo?'#444':'gold'}; color:${jaSigo?'white':'black'}" onclick="seguir('${p.autorEmail}')">${jaSigo?'✅ Seguindo':'👤 Seguir'}</button>` : ''}
                    ${eMeu ? `<button class="btn-interagir" style="background:#e74c3c" onclick="removerPost(${p.id})">🗑️</button>` : ''}
                </div>
            </div>`;
            return d;
        }

        function postarFoto() {
            const f = document.getElementById('input-post').files[0], cat = document.getElementById('post-cat').value;
            if(!f) return alert("Selecione!");
            const r = new FileReader(); r.onload = (e) => {
                let c = JSON.parse(localStorage.getItem(usuarioAtual)) || { posts: [] };
                c.posts.unshift({ id: Date.now(), imagem: e.target.result, descricao: document.getElementById('post-desc').value, categoria: cat, likes: 0, comentarios: [] });
                localStorage.setItem(usuarioAtual, JSON.stringify(c)); carregarPerfil(); toggleElement('postar-foto');
            }; r.readAsDataURL(f);
        }

        function salvarPerfil() {
            let c = JSON.parse(localStorage.getItem(usuarioAtual)) || {}; 
            c.bio = document.getElementById('input-bio').value;
            const f = document.getElementById('input-foto').files[0];
            if(f) { const r = new FileReader(); r.onload = (e) => { c.foto = e.target.result; localStorage.setItem(usuarioAtual, JSON.stringify(c)); carregarPerfil(); }; r.readAsDataURL(f); }
            else { localStorage.setItem(usuarioAtual, JSON.stringify(c)); carregarPerfil(); }
            toggleElement('edit-perfil');
        }

        function removerPost(id) {
            let c = JSON.parse(localStorage.getItem(usuarioAtual)) || { posts: [] }; 
            c.posts = c.posts.filter(p => p.id !== id);
            localStorage.setItem(usuarioAtual, JSON.stringify(c)); carregarPerfil();
        }

        function interagir(email, id, acao) {
            let c = JSON.parse(localStorage.getItem(email)) || { posts: [] }; 
            const p = c.posts.find(x => x.id === id);
            if(p && acao === 'like') p.likes++;
            localStorage.setItem(email, JSON.stringify(c)); carregarFeed('feed-global', 'todas');
        }

        function deletarConta() { if(confirm("Certeza?")) { localStorage.removeItem(usuarioAtual); logout(); } }
        function toggleElement(id) { const e = document.getElementById(id); e.style.display = e.style.display === 'none' ? 'block' : 'none'; }
    </script>
</body>
</html>
