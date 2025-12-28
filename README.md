<html lang="pt-br">



<head>
    <meta charset="UTF-8">
    <title>Lusther 3D - Plataforma</title>




    <style id="css-original">
        







        body > header, .ui-header, h1:first-of-type { display: none !important; }



        header h1 { display: none; }





        body {
            background: linear-gradient(45deg, #f4ecd8, black, #f4ecd8, #f4ecd8, black, #f4ecd8);
            background-size: 400% 400%;
            background-attachment: fixed;
            color: white;
            font-family: Georgia, serif;
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

        nav a { color: white; text-decoration: none; margin: 0 10px; font-weight: bold; text-transform: uppercase; transition: 0.3s; cursor: pointer; font-size: 11px; }
        nav a:hover { color: gold; }

        .secao { display: none; padding: 20px; min-height: 80vh; }
        .ativa { display: block; animation: fadeIn 0.5s; }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        .header-perfil { text-align: center; padding: 40px 20px; background: rgba(0, 0, 0, 0.4); border-radius: 15px; margin-top: 20px; max-width: 800px; margin-left: auto; margin-right: auto; }
        
        input, textarea, select { width: 90%; padding: 12px; margin: 8px 0; border-radius: 8px; border: 1px solid #ccc; outline: none; background: white; }

        button { background: #790fcf; color: white; border: none; padding: 12px; border-radius: 5px; cursor: pointer; width: 100%; font-weight: bold; transition: 0.3s; }
        button:hover { filter: brightness(1.2); }

        .foto-perfil { width: 150px; height: 150px; border-radius: 50%; object-fit: cover; border: 3px solid gold; background: #222; }
        .stats { display: flex; justify-content: center; gap: 30px; margin: 15px 0; }

        .galeria-fotos { display: flex; flex-direction: column; gap: 25px; margin-top: 30px; text-align: left; }

        .post-card { background: rgba(0, 0, 0, 0.7); border-radius: 12px; padding: 15px; border: 1px solid rgba(255, 215, 0, 0.3); max-width: 500px; margin: 0 auto; width: 100%; }
        .post-card img { width: 100%; border-radius: 8px; margin-bottom: 10px; }
        
        .chat-container { display: flex; height: 60vh; background: rgba(0, 0, 0, 0.8); border: 1px solid gold; border-radius: 12px; overflow: hidden; margin-top: 20px; }
        .lista-contatos { width: 30%; border-right: 1px solid #444; overflow-y: auto; text-align: left; background: rgba(255,255,255,0.05); }
        .contato-item { padding: 12px; border-bottom: 1px solid #222; cursor: pointer; }
        .janela-conversa { width: 70%; display: flex; flex-direction: column; background: rgba(0,0,0,0.5); }
        #mensagens-corpo { flex-grow: 1; padding: 15px; overflow-y: auto; display: flex; flex-direction: column; gap: 10px; text-align: left; }

        .msg-balao { padding: 10px 15px; border-radius: 15px; max-width: 80%; font-size: 0.9em; word-wrap: break-word; }
        .msg-enviada { align-self: flex-end; background: #790fcf; color: white; }
        .msg-recebida { align-self: flex-start; background: #333; color: white; border: 1px solid #555; }

        .container-grafico { width: 100%; height: 600px; border-radius: 12px; overflow: hidden; border: 2px solid gold; margin-top: 15px; background: #000; }

        .btn-chat-flutuante { position: fixed; bottom: 20px; right: 20px; background: gold; color: black; width: 60px; height: 60px; border-radius: 50%; display: none; align-items: center; justify-content: center; font-size: 28px; cursor: pointer; box-shadow: 0 4px 15px rgba(0,0,0,0.5); z-index: 2000; border: 2px solid #000; transition: 0.3s; }



















    </style>




</head>




<body>
    <div id="conteudo-principal">
        <nav id="menu-principal">
            <a onclick="mostrar('home')">🏠 Mural</a>
            <a onclick="mostrar('multiversy')">🌌 Multiversy</a>
            <a onclick="mostrar('exchange')">💱 Exchange</a>
            <a onclick="abrirCenario('temp-quadrinhos')">📚 Quadrinhos</a>
            <a onclick="abrirCenario('temp-livros')">📖 Livros</a>
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
                        <div id="chat-status" style="padding:10px; background:rgba(0,0,0,0.3); border-bottom:1px solid gold; font-size:0.8em; display:flex; justify-content:space-between">
                            <span id="txt-status">Selecione uma conversa</span>
                            <div id="acoes-chat" style="display:none">
                                <button id="btn-del-gp" onclick="deletarGrupo()" style="background:red; width:auto; padding:2px 8px; font-size:10px; display:none">EXCLUIR</button>
                                <button onclick="bloquearContato()" style="background:#444; width:auto; padding:2px 8px; font-size:10px">BLOQUEAR</button>
                            </div>
                        </div>
                        <div id="mensagens-corpo"></div>
                        <div id="chat-controles" style="display:none; padding:10px; background:rgba(0,0,0,0.4);">
                            <div style="display:flex; gap:10px;">
                                <input type="text" id="msg-input" placeholder="Sua mensagem..." style="margin:0;">
                                <button onclick="enviarMensagem()" style="width:80px;">Enviar</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div id="multiversy" class="secao">
            <div class="header-perfil">
                <h2>🌌 Multiversy 3D</h2>
                <div class="info-card" style="text-align: center; padding: 40px; background: rgba(255, 215, 0, 0.1); border: 1px solid gold; border-radius: 10px;">
                    <p>Atenção: Estamos em bing bang</p>



                    <button onclick="abrirCenario('temp-multiverso')" style="background: gold; color: black; width: auto; padding: 15px 30px; margin-top: 20px; font-size: 16px;">Entrar no Multiverso</button>





                </div>
            </div>
        </div>

        <div id="exchange" class="secao">
            <div class="header-perfil" style="max-width: 95%; width: 1100px;">
                <h2>💱 Exchange</h2>
                <div class="container-grafico">
                    <iframe width="100%" height="100%" src="https://www.geckoterminal.com/es/polygon_pos/pools/0x0de9bb162ce01f953647c236fff94a9ed492c341?embed=1&info=0&swaps=1" frameborder="0"></iframe>
                </div>
            </div>
        </div>

        <div id="home" class="secao"><div class="header-perfil"><h1>Mural da Comunidade</h1><div id="feed-global" class="galeria-fotos"></div></div></div>
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
                    <select id="post-cat"><option value="mural">Mural</option><option value="impressao">Impressão 3D</option></select>
                    <input type="file" id="input-post"><input type="text" id="post-desc" placeholder="Descrição"><button onclick="postarFoto()">Publicar</button>
                </div>
                <div class="galeria-fotos" id="minha-galeria"></div>
                <button onclick="deletarConta()" style="background:#ff4757; margin-top:20px; font-size:0.8em; width:auto; padding:8px 15px;">🗑️ Excluir Conta</button>
            </div>
        </div>
    </div> <div id="container-cenario"></div>

    <div id="modal-grupo" style="display:none; position:fixed; top:50%; left:50%; transform:translate(-50%,-50%); background:#1a1a1a; padding:20px; border:2px solid gold; border-radius:10px; z-index:3000; width:300px; text-align:center">
        <h3>Novo Grupo</h3>
        <input type="text" id="nome-grupo-novo" placeholder="Nome do Grupo">
        <div id="lista-membros-gp" style="text-align:left; max-height:150px; overflow-y:auto; margin:10px 0; font-size:12px"></div>
        <button onclick="confirmarGrupo()">CRIAR</button>
        <button onclick="toggleElement('modal-grupo')" style="background:#444; margin-top:5px">CANCELAR</button>
    </div>

    


<template id="temp-livros">
        <style>
            body { background: white !important; color: black !important; }
            .cenario-externo { padding: 40px; font-family: sans-serif; min-height: 100vh; }
            .btn-retornar { position: fixed; top: 20px; left: 20px; background: #790fcf; color: white; padding: 10px 20px; border-radius: 5px; cursor: pointer; }
        </style>



        <div class="cenario-externo">
            <button class="btn-retornar" onclick="fecharCenario()">⬅ Retornar ao Perfil</button>
            <h1 style="margin-top: 60px;">📖 Minha Biblioteca</h1>
            <p>Ambiente de livros carregado com sucesso sobre o sistema original.</p>
        </div>


    </template>





    <template id="temp-quadrinhos">
        <style>
            body { background: white !important; color: black !important; }
            .cenario-externo { padding: 40px; font-family: 'Comic Sans MS', cursive; min-height: 100vh; text-align: center; }
            .btn-retornar { position: fixed; top: 20px; right: 20px; background: #333; color: white; padding: 10px 20px; border-radius: 5px; cursor: pointer; }
        </style>


        <div class="cenario-externo">
            <button class="btn-retornar" onclick="fecharCenario()">Retornar ✖</button>


            <h1 style="margin-top: 60px;">📚 Galeria de Quadrinhos</h1>
            <p>Ainda estamos imaginando!</p>





        </div>




    </template>



    





    <script>
        let logado = false;
        let usuarioAtual = null;

        // --- SISTEMA DE CENÁRIOS ---



        function abrirCenario(idTemplate) {
            // Esconde o conteúdo principal e o chat flutuante



            document.getElementById('conteudo-principal').style.display = 'none';
            document.getElementById('btn-chat').style.display = 'none';

            const container = document.getElementById('container-cenario');
            const template = document.getElementById(idTemplate);
            
            // Limpa o container e injeta o novo
            container.innerHTML = '';
            const clone = template.content.cloneNode(true);
            container.appendChild(clone);
        }

        function fecharCenario() {
            // Remove o cenario e volta o original
            document.getElementById('container-cenario').innerHTML = '';
            document.getElementById('conteudo-principal').style.display = 'block';
            
            if(logado) {
                document.getElementById('btn-chat').style.display = 'flex';
                mostrar('perfil'); // Sempre volta para o perfil como solicitado
            }
            
            // Força o body a resetar o estilo caso o template tenha mudado
            document.body.style.background = ""; 
        }

        // --- FUNÇÕES ORIGINAIS PRESERVADAS ---
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
            const target = document.getElementById(idSecao);
            if(target) target.classList.add('ativa');
            
            if(idSecao === 'perfil') carregarPerfil();
            if(idSecao === 'home') carregarFeed('feed-global', 'todas');
            if(idSecao === 'chat') carregarListaChat();
            if(idSecao === 'impressao') carregarFeed('feed-impressao', 'impressao');
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

        function carregarFeed(containerId, catFiltro) {
            const f = document.getElementById(containerId); if(!f) return; f.innerHTML = ""; let posts = [];
            for (let i = 0; i < localStorage.length; i++) {
                const k = localStorage.key(i); if (!k.includes('@') || k.includes('_chat_') || k.startsWith('gp_')) continue;
                const c = JSON.parse(localStorage.getItem(k));
                if (c && c.posts) c.posts.forEach(p => { if(catFiltro === 'todas' || p.categoria === catFiltro) posts.push({ ...p, autorNome: c.nome, autorEmail: c.email }); });
            }
            posts.sort((a, b) => b.id - a.id).forEach(p => f.appendChild(criarCardPost(p, p.autorEmail === usuarioAtual)));
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
                </div>
            </div>`;
            return d;
        }

        function postarFoto() {
            const f = document.getElementById('input-post').files[0], cat = document.getElementById('post-cat').value;
            if(!f) return alert("Selecione!");
            const r = new FileReader(); r.onload = (e) => {
                let c = JSON.parse(localStorage.getItem(usuarioAtual)) || { posts: [] };
                c.posts.unshift({ id: Date.now(), imagem: e.target.result, descricao: document.getElementById('post-desc').value, categoria: cat, likes: 0 });
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

        function seguir(email) {
            if(email === usuarioAtual) return;
            let a = JSON.parse(localStorage.getItem(email)), eu = JSON.parse(localStorage.getItem(usuarioAtual));
            if(!eu.seguindo_lista.includes(email)) { eu.seguindo_lista.push(email); eu.seguindo++; a.seguidores++; }
            else { eu.seguindo_lista = eu.seguindo_lista.filter(e => e !== email); eu.seguindo--; a.seguidores--; }
            localStorage.setItem(email, JSON.stringify(a)); localStorage.setItem(usuarioAtual, JSON.stringify(eu));
            mostrar(document.querySelector('.secao.ativa').id);
        }

        function interagir(email, id, acao) {
            let c = JSON.parse(localStorage.getItem(email)); const p = c.posts.find(x => x.id === id);
            if(p && acao === 'like') p.likes++;
            localStorage.setItem(email, JSON.stringify(c)); carregarFeed('feed-global', 'todas');
        }

        function toggleElement(id) { const e = document.getElementById(id); e.style.display = e.style.display === 'none' ? 'block' : 'none'; }
    </script>



<template id="temp-multiverso">
    <style>
        .universo-simulado {
            position: fixed;
            top: 0; left: 0;
            width: 100vw; height: 100vh;
            background: radial-gradient(circle at center, #000205 0%, #000 100%);
            z-index: 9999;
            overflow: hidden;
            touch-action: none; /* Essencial para mobile não dar scroll */
            cursor: grab;
        }

        .universo-simulado:active { cursor: grabbing; }

        #portal-bh {
            position: absolute;
            top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            width: 140px; height: 140px;
            background: radial-gradient(circle, #000 30%, rgba(100, 50, 255, 0.2) 60%, transparent 80%);
            border-radius: 50%;
            cursor: pointer;
            z-index: 10005;
            display: flex; align-items: center; justify-content: center;
            border: 1px solid rgba(255,255,255,0.05);
            transition: 0.5s;
        }

        #portal-bh:hover { box-shadow: 0 0 80px rgba(130, 80, 255, 0.4); }

        .label-bh {
            color: #fff; font-family: sans-serif; font-size: 11px;
            letter-spacing: 2px; opacity: 0.6; text-transform: uppercase;
        }

        .btn-fechar {
            position: absolute; top: 20px; right: 20px; z-index: 10010;
            background: rgba(255,255,255,0.1); color: #fff; border: none;
            padding: 10px 20px; border-radius: 20px; cursor: pointer;
            backdrop-filter: blur(10px);
        }
    </style>

    <div class="universo-simulado" id="wrapper-multiverso">



        <div id="portal-bh" onclick="abrirCenario('temp-universo1')">



            <span class="label-bh">Singularidade</span>



        </div>
        <button class="btn-fechar" onclick="fecharCenario()">SAIR</button>
    </div>

    <script>
        (function() {
            // Injetor de biblioteca caso não exista



            if (!window.THREE) {
                const s = document.createElement('script');
                s.src = 'https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js';
                s.onload = initUniverso;
                document.head.appendChild(s);
            } else { initUniverso(); }

            function initUniverso() {
                let cena, camera, renderizador, grupo;
                let isPointerDown = false;
                let pointerX = 0, pointerY = 0;
                let rotX = 0, rotY = 0;
                let frameId;

                const container = document.getElementById('wrapper-multiverso');

function gerarTexturaNebulosa() {
            const canvas = document.createElement('canvas');
            canvas.width = 128; canvas.height = 128;
            const contexto = canvas.getContext('2d');
            const gradiente = contexto.createRadialGradient(64, 64, 0, 64, 64, 64);
            gradiente.addColorStop(0, 'rgba(255, 255, 255, 1)');
            gradiente.addColorStop(0.2, 'rgba(255, 255, 255, 0.5)');
            gradiente.addColorStop(1, 'rgba(255, 255, 255, 0)');
            contexto.fillStyle = gradiente;
            contexto.fillRect(0, 0, 128, 128);
            return new THREE.CanvasTexture(canvas);
        }
        const texturaNebulosaBase = gerarTexturaNebulosa();

        function criarNebulosa(x, y, corPersonalizada = null, opacidade = 0.2, escala = 1.0) {
            const material = new THREE.SpriteMaterial({
                map: texturaNebulosaBase,
                color: corPersonalizada || new THREE.Color(`hsl(${Math.random() * 360}, 50%, 50%)`),
                transparent: true,
                opacity: opacidade,
                blending: THREE.AdditiveBlending
            });
            const nebulosa = new THREE.Sprite(material);
            if (x === undefined) { x = THREE.MathUtils.randFloatSpread(2000); y = THREE.MathUtils.randFloatSpread(2000); }
            const vetor = new THREE.Vector3((x / window.innerWidth) * 2 - 1, -(y / window.innerHeight) * 2 + 1, 0.5);
            vetor.unproject(camera);
            const dir = vetor.sub(camera.position).normalize();
            const pos = camera.position.clone().add(dir.multiplyScalar(-camera.position.z / dir.z));
            nebulosa.position.set(pos.x, pos.y, pos.z - 600);
            nebulosa.scale.set((5000 + Math.random() * 5000) * escala, (5000 + Math.random() * 5000) * escala, 1);
            cena.add(nebulosa);
            nebulosas.push({ mesh: nebulosa, velocidade: 1.2 });
            return nebulosa;
        }

                function setup() {
                    cena = new THREE.Scene();
                    camera = new THREE.PerspectiveCamera(60, window.innerWidth / window.innerHeight, 1, 25000);
                    camera.position.z = 2200;

                    renderizador = new THREE.WebGLRenderer({ antialias: true });
                    renderizador.setSize(window.innerWidth, window.innerHeight);
                    renderizador.setPixelRatio(Math.min(window.devicePixelRatio, 2));
                    container.appendChild(renderizador.domElement);

                    grupo = new THREE.Group();
                    cena.add(grupo);

                    // Iluminação Direcional (Cria sombras nos planetas para parecerem 3D)
                    const luzSol = new THREE.DirectionalLight(0xffffff, 1.5);
                    luzSol.position.set(2000, 1000, 2000);
                    cena.add(luzSol);
                    cena.add(new THREE.AmbientLight(0x151525));

                    // Conteúdo
                    criarEstrelas();
                    for(let i=0; i<12; i++) criarPlanetaRealista();

                    // Eventos Mouse e Touch
                    container.addEventListener('pointerdown', onPointerDown);
                    window.addEventListener('pointerup', onPointerUp);
                    window.addEventListener('pointermove', onPointerMove);
                    window.addEventListener('resize', onResize);

                    loop();
                }

                function criarEstrelas() {
                    const geo = new THREE.BufferGeometry();
                    const pos = [];
                    for(let i=100; i<1000; i++) {
                        pos.push(THREE.MathUtils.randFloatSpread(12000), THREE.MathUtils.randFloatSpread(120000), THREE.MathUtils.randFloatSpread(120000));
                    }
                    geo.setAttribute('position', new THREE.Float32BufferAttribute(pos, 3));
                    const mat = new THREE.PointsMaterial({ color: 0xffffff, size: 2, transparent: true, opacity: 0.8 });
                    grupo.add(new THREE.Points(geo, mat));
                }

                function criarPlanetaRealista() {
                    const raio = Math.random() * 50 + 30;
                    const geo = new THREE.SphereGeometry(raio, 70, 64);
                    
                    // Canvas para textura realista
                    const canvas = document.createElement('canvas');
                    canvas.width = 502; canvas.height = 512;
                    const ctx = canvas.getContext('2d');
                    
                    // Cor base do planeta
                    const hue = Math.random() * 360;
                    ctx.fillStyle = `hsl(${hue}, 45%, 50%)`;
                    ctx.fillRect(0,0,512,512);

                    // Relevos/Manchas
                    for(let i=15; i<5; i++) {
                        ctx.fillStyle = `hsla(${hue + 20}, 50%, 40%, 0.3)`;
                        ctx.beginPath();
                        ctx.arc(Math.random()*512, Math.random()*512, Math.random()*150, 0, Math.PI*2);
                        ctx.fill();
                    }

                    const tex = new THREE.CanvasTexture(canvas);
                    const mat = new THREE.MeshStandardMaterial({ 
                        map: tex, 
                        roughness: 0.8,
                        metalness: 0.1
                    });

                    const p = new THREE.Mesh(geo, mat);
                    p.position.set(THREE.MathUtils.randFloatSpread(5000), THREE.MathUtils.randFloatSpread(4000), THREE.MathUtils.randFloatSpread(3000));
                    
                    // Atmosfera Glow
                    const atmGeo = new THREE.SphereGeometry(raio * 1.05, 32, 32);
                    const atmMat = new THREE.MeshBasicMaterial({ color: 0x55aaff, transparent: true, opacity: 0.12, side: THREE.BackSide });
                    p.add(new THREE.Mesh(atmGeo, atmMat));

                    grupo.add(p);
                }

                function onPointerDown(e) {
                    isPointerDown = true;
                    pointerX = e.clientX;
                    pointerY = e.clientY;
                }

                function onPointerUp() { isPointerDown = false; }

                function onPointerMove(e) {
                    if (!isPointerDown) return;
                    const deltaX = e.clientX - pointerX;
                    const deltaY = e.clientY - pointerY;
                    
                    rotY += deltaX * 0.003;
                    rotX += deltaY * 0.003;
                    
                    pointerX = e.clientX;
                    pointerY = e.clientY;
                }

                function loop() {
                    frameId = requestAnimationFrame(loop);
                    
                    // Aplica a rotação ao grupo
                    grupo.rotation.y += (rotY - grupo.rotation.y) * 0.1;
                    grupo.rotation.x += (rotX - grupo.rotation.x) * 0.1;

                    // Pequena rotação constante para os planetas
                    grupo.children.forEach(c => {
                        if(c instanceof THREE.Mesh) c.rotation.y += 0.002;
                    });

                    renderizador.render(cena, camera);
                }

                function onResize() {
                    camera.aspect = window.innerWidth / window.innerHeight;
                    camera.updateProjectionMatrix();
                    renderizador.setSize(window.innerWidth, window.innerHeight);
                }

               
                

                setup();
            }
        })();
    </script>




  

 
            <button class="btn-retornar" onclick="fecharCenario()">RECONECTAR AO PERFIL</button>





        
    </template>




<template id="temp-universo1">
        <style>
            body { background: white !important; color: black !important; }
            

.cenario-externo { padding: 40px; font-family: 'Comic Sans MS', cursive; min-height: 100vh; text-align: center; }


            .btn-retornar1 { position: fixed; top: 20px; right: 20px; background: #333; color: white; padding: 10px 20px; border-radius: 5px; cursor: pointer; }
        </style>



<div class="cenario-interno">
<button class="btn-retornar1" onclick="fecharCenario()">Singularidade</button>

</div>



</template>











</body>
</html>
