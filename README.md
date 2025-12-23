
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

        /* Estilo específico para o Iframe do Gráfico */
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

    <div id="multiversy" class="secao">
        <div class="header-perfil">
            <h2>🌌 Multiversy</h2>
            <div class="info-card">
                <p>Bem-vindo ao Multiversy. Esta é uma área exclusiva para exploração de conteúdos especiais.</p>
                <p><i>Conteúdo em desenvolvimento...</i></p>
            </div>
        </div>
    </div>

    <div id="exchange" class="secao">
        <div class="header-perfil" style="max-width: 95%; width: 1100px;">
            <h2>💱 Exchange Lusther 3D</h2>
            <p style="font-size: 0.8em; color: gold; margin-bottom: 10px;">Token: 0x1132d4835542334f95f9aa48247ad9cc37b286d7 (Polygon)</p>
            
            <div class="container-grafico">
                <iframe 
                    width="100%" 
                    height="100%" 
                    id="geckoterminal-embed" 
                    title="GeckoTerminal Embed" 
                    src="https://www.geckoterminal.com/es/polygon_pos/pools/0x0de9bb162ce01f953647c236fff94a9ed492c341?embed=1&info=0&swaps=1" 
                    frameborder="0" 
                    allow="clipboard-write" 
                    allowfullscreen>
                </iframe>
            </div>
            
            <div style="margin-top: 15px; display: flex; gap: 10px; justify-content: center;">
                <button onclick="window.open('https://www.geckoterminal.com/es/polygon_pos/pools/0x0de9bb162ce01f953647c236fff94a9ed492c341', '_blank')" style="width: auto; background: #3498db; padding: 10px 20px;">Ver no GeckoTerminal ↗</button>
            </div>
        </div>
    </div>

    <div id="home" class="secao"><div class="header-perfil"><h1>Mural da Comunidade</h1><div id="feed-global" class="galeria-fotos"></div></div></div>
    <div id="quadrinhos" class="secao"><div class="header-perfil"><h2>📚 Quadrinhos</h2><div id="feed-quadrinhos" class="galeria-fotos"></div></div></div>
    <div id="livros" class="secao"><div class="header-perfil"><h2>📖 Livros</h2><div id="feed-livros" class="galeria-fotos"></div></div></div>
    <div id="impressao" class="secao"><div class="header-perfil"><h2>⚙️ Impressão 3D</h2><div id="feed-impressao" class="galeria-fotos"></div></div></div>

    <div id="perfil" class="secao">
        <div class="header-perfil">
            <img id="display-foto" src="https://via.placeholder.com/150" class="foto-perfil">
            <h2 id="display-nome">Carregando...</h2>
            <p id="display-bio">...</p>
            <div class="stats">
                <div><span id="num-seguidores">0</span><br>Seguidores</div>
                <div><span id="num-seguindo">0</span><br>Seguindo</div>
            </div>
            <div style="display: flex; gap: 10px; justify-content: center;">
                <button onclick="toggleElement('edit-perfil')" style="width: auto; background: #555;">⚙️ Editar Perfil</button>
                <button onclick="toggleElement('postar-foto')" style="width: auto; background: gold; color: black;">📸 Postar Algo</button>
            </div>

            <div id="edit-perfil" style="display:none; margin-top: 20px; background: rgba(0,0,0,0.5); padding: 15px; border-radius: 10px;">
                <input type="file" id="input-foto" accept="image/*">
                <textarea id="input-bio" placeholder="Sua nova bio..."></textarea>
                <button onclick="salvarPerfil()" style="background: #2ecc71;">Atualizar</button>
            </div>

            <div id="postar-foto" style="display:none; margin-top: 20px; background: rgba(0,0,0,0.5); padding: 15px; border-radius: 10px; text-align: left;">
                <label>Categoria:</label>
                <select id="post-cat">
                    <option value="mural">Mural Geral</option>
                    <option value="quadrinhos">Quadrinhos</option>
                    <option value="livros">Livros</option>
                    <option value="impressao">Impressão 3D</option>
                </select>
                <input type="file" id="input-post" accept="image/*">
                <input type="text" id="post-desc" placeholder="Descrição...">
                <input type="text" id="post-tags" placeholder="Hashtags...">
                <button onclick="postarFoto()" style="background: #3498db;">Publicar</button>
            </div>

            <hr style="margin: 30px 0; border: 0; border-top: 1px solid gold;">
            <h3>Minhas Postagens</h3>
            <div class="galeria-fotos" id="minha-galeria"></div>
            <button onclick="deletarConta()" class="btn-perigo">🗑️ Excluir Minha Conta</button>
        </div>
    </div>

    <script>
        let logado = false;
        let usuarioAtual = null;

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
            if(idSecao === 'quadrinhos') carregarFeed('feed-quadrinhos', 'quadrinhos');
            if(idSecao === 'livros') carregarFeed('feed-livros', 'livros');
            if(idSecao === 'impressao') carregarFeed('feed-impressao', 'impressao');
        }

        function alternarTela(t) { 
            document.getElementById('area-login').style.display = t === 'login' ? 'block' : 'none';
            document.getElementById('area-cadastro').style.display = t === 'cadastro' ? 'block' : 'none';
        }

        function cadastrarUsuario() {
            const n = document.getElementById('cad-nome').value, e = document.getElementById('cad-email').value, s = document.getElementById('cad-senha').value;
            if(!n || !e || !s) return alert("Preencha tudo!");
            if(localStorage.getItem(e)) return alert("Já existe!");
            localStorage.setItem(e, JSON.stringify({ nome: n, email: e, senha: s, bio: "", foto: "", posts: [], seguidores: 0, seguindo: 0 }));
            alert("Sucesso!"); alternarTela('login');
        }

        function realizarLogin() {
            const e = document.getElementById('login-email').value, s = document.getElementById('login-senha').value, c = JSON.parse(localStorage.getItem(e));
            if(c && c.senha === s) { localStorage.setItem('sessao_ativa', e); loginSucesso(c); } else alert("Erro!");
        }

        function loginSucesso(c) { logado = true; usuarioAtual = c.email; document.getElementById('menu-principal').style.display = 'block'; mostrar('home'); }
        function logout() { localStorage.removeItem('sessao_ativa'); location.reload(); }

        function carregarFeed(containerId, catFiltro) {
            const f = document.getElementById(containerId); f.innerHTML = ""; let posts = [];
            for (let i = 0; i < localStorage.length; i++) {
                const k = localStorage.key(i); if (k === 'sessao_ativa' || !k.includes('@')) continue;
                const c = JSON.parse(localStorage.getItem(k));
                if (c.posts) c.posts.forEach(p => { if(catFiltro === 'todas' || p.categoria === catFiltro) posts.push({ ...p, autorNome: c.nome, autorEmail: c.email }); });
            }
            posts.sort((a, b) => b.id - a.id).forEach(p => f.appendChild(criarCardPost(p, p.autorEmail === usuarioAtual)));
        }

        function carregarPerfil() {
            const c = JSON.parse(localStorage.getItem(usuarioAtual));
            document.getElementById('display-nome').innerText = c.nome;
            document.getElementById('display-bio').innerText = c.bio || "Sem bio.";
            document.getElementById('display-foto').src = c.foto || "https://via.placeholder.com/150";
            document.getElementById('num-seguidores').innerText = c.seguidores;
            document.getElementById('num-seguindo').innerText = c.seguindo;
            const g = document.getElementById('minha-galeria'); g.innerHTML = "";
            if(c.posts) c.posts.forEach(p => g.appendChild(criarCardPost({...p, autorNome: c.nome, autorEmail: c.email}, true)));
        }

        function criarCardPost(p, eMeu) {
            const d = document.createElement('div'); d.className = 'post-card';
            d.innerHTML = `<span class="post-categoria">${p.categoria}</span><img src="${p.imagem}"><div class="post-info">
                <p><strong>${p.autorNome}</strong> ${p.descricao}</p><p class="post-tags">${p.hashtags}</p>
                <div class="btn-group">
                    <button class="btn-interagir" onclick="interagir('${p.autorEmail}', ${p.id}, 'like')">❤️ ${p.likes}</button>
                    <button class="btn-interagir" style="background:#444" onclick="interagir('${p.autorEmail}', ${p.id}, 'comment')">💬 Comentar</button>
                    ${!eMeu ? `<button class="btn-interagir" style="background:gold;color:black" onclick="seguir('${p.autorEmail}')">👤 Seguir</button>` : ''}
                    ${eMeu ? `<button class="btn-interagir" style="background:#e74c3c" onclick="removerPost(${p.id})">🗑️</button>` : ''}
                </div>
                <div class="comentarios-area">${p.comentarios.map(c => `<div class="comentario-item"><strong>${c.autor}:</strong> ${c.texto}</div>`).join('')}</div>
            </div>`;
            return d;
        }

        function postarFoto() {
            const f = document.getElementById('input-post').files[0], cat = document.getElementById('post-cat').value;
            if(!f) return alert("Selecione!");
            const r = new FileReader(); r.onload = (e) => {
                let c = JSON.parse(localStorage.getItem(usuarioAtual));
                c.posts.unshift({ id: Date.now(), imagem: e.target.result, descricao: document.getElementById('post-desc').value, hashtags: document.getElementById('post-tags').value, categoria: cat, likes: 0, comentarios: [] });
                localStorage.setItem(usuarioAtual, JSON.stringify(c)); alert("Postado!"); carregarPerfil(); toggleElement('postar-foto');
            }; r.readAsDataURL(f);
        }

        function interagir(email, id, acao) {
            let c = JSON.parse(localStorage.getItem(email)); const p = c.posts.find(x => x.id === id);
            if(acao === 'like') p.likes++;
            if(acao === 'comment') { const m = prompt("Comente:"); if(m) p.comentarios.push({ autor: JSON.parse(localStorage.getItem(usuarioAtual)).nome, texto: m }); }
            localStorage.setItem(email, JSON.stringify(c)); mostrar(document.querySelector('.secao.ativa').id);
        }

        function seguir(email) {
            let a = JSON.parse(localStorage.getItem(email)), eu = JSON.parse(localStorage.getItem(usuarioAtual));
            a.seguidores++; eu.seguindo++; localStorage.setItem(email, JSON.stringify(a)); localStorage.setItem(usuarioAtual, JSON.stringify(eu));
            alert("Seguindo!"); carregarPerfil();
        }

        function salvarPerfil() {
            let c = JSON.parse(localStorage.getItem(usuarioAtual)); c.bio = document.getElementById('input-bio').value || c.bio;
            const f = document.getElementById('input-foto').files[0];
            if(f) { const r = new FileReader(); r.onload = (e) => { c.foto = e.target.result; localStorage.setItem(usuarioAtual, JSON.stringify(c)); carregarPerfil(); }; r.readAsDataURL(f); }
            else { localStorage.setItem(usuarioAtual, JSON.stringify(c)); carregarPerfil(); }
            toggleElement('edit-perfil');
        }

        function removerPost(id) {
            let c = JSON.parse(localStorage.getItem(usuarioAtual)); c.posts = c.posts.filter(p => p.id !== id);
            localStorage.setItem(usuarioAtual, JSON.stringify(c)); carregarPerfil();
        }

        function deletarConta() { if(confirm("Certeza?")) { localStorage.removeItem(usuarioAtual); logout(); } }
        function toggleElement(id) { const e = document.getElementById(id); e.style.display = e.style.display === 'none' ? 'block' : 'none'; }
    </script>
</body>
</html>
