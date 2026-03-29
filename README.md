# loja-caneleiras
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>EMF Loja Online</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      background: #f5f5f5;
      color: #222;
    }

    /* TOPO */
    .topbar {
      background: #111;
      color: white;
      padding: 15px 25px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
      flex-wrap: wrap;
    }

    .logo {
      font-size: 28px;
      font-weight: bold;
      color: #00cc66;
    }

    .search-box {
      flex: 1;
      max-width: 500px;
      display: flex;
    }

    .search-box input {
      width: 100%;
      padding: 12px;
      border: none;
      outline: none;
      border-radius: 8px 0 0 8px;
      font-size: 15px;
    }

    .search-box button {
      padding: 12px 18px;
      border: none;
      background: #00cc66;
      color: black;
      font-weight: bold;
      cursor: pointer;
      border-radius: 0 8px 8px 0;
    }

    .menu-top {
      display: flex;
      gap: 15px;
      font-size: 14px;
    }

    .menu-top a {
      color: white;
      text-decoration: none;
    }

    .menu-top a:hover {
      color: #00cc66;
    }

    /* CONTAINER */
    .container {
      display: flex;
      gap: 20px;
      padding: 20px;
    }

    /* SIDEBAR */
    .sidebar {
      width: 220px;
      background: white;
      padding: 20px;
      border-radius: 15px;
      height: fit-content;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
    }

    .sidebar h3 {
      margin-bottom: 15px;
      color: #00aa55;
      font-size: 18px;
    }

    .sidebar ul {
      list-style: none;
    }

    .sidebar li {
      margin-bottom: 12px;
      font-size: 15px;
      cursor: pointer;
      color: #333;
      transition: 0.2s;
    }

    .sidebar li:hover {
      color: #00aa55;
      transform: translateX(3px);
    }

    /* MAIN */
    .main {
      flex: 1;
    }

    .titulo-loja {
      font-size: 30px;
      margin-bottom: 15px;
      color: #111;
    }

    .filtros {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      margin-bottom: 20px;
    }

    .filtro {
      background: white;
      border: 1px solid #ddd;
      padding: 10px 14px;
      border-radius: 10px;
      cursor: pointer;
      font-size: 14px;
      transition: 0.2s;
    }

    .filtro:hover {
      background: #00cc66;
      color: black;
      border-color: #00cc66;
    }

    /* PRODUTOS */
    .grid-produtos {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
      gap: 18px;
    }

    .produto {
      background: white;
      border-radius: 15px;
      overflow: hidden;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
      transition: 0.25s;
    }

    .produto:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 18px rgba(0,0,0,0.12);
    }

    .produto img {
      width: 100%;
      height: 220px;
      object-fit: cover;
      cursor: pointer;
    }

    .produto-info {
      padding: 15px;
    }

    .produto h4 {
      font-size: 15px;
      margin-bottom: 8px;
      min-height: 40px;
    }

    .avaliacao {
      color: #f4b400;
      font-size: 14px;
      margin-bottom: 8px;
    }

    .preco-antigo {
      text-decoration: line-through;
      color: #999;
      font-size: 14px;
    }

    .preco {
      color: #00aa55;
      font-size: 28px;
      font-weight: bold;
      margin: 6px 0 12px;
    }

    .btn-ver {
      width: 100%;
      padding: 10px;
      border: none;
      border-radius: 10px;
      background: #111;
      color: white;
      font-weight: bold;
      cursor: pointer;
      transition: 0.2s;
    }

    .btn-ver:hover {
      background: #00cc66;
      color: black;
    }

    /* MODAL IMAGEM */
    .modal {
      display: none;
      position: fixed;
      z-index: 999;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.9);
      justify-content: center;
      align-items: center;
      padding: 20px;
    }

    .modal img {
      max-width: 90%;
      max-height: 90%;
      border-radius: 15px;
    }

    .fechar {
      position: absolute;
      top: 20px;
      right: 30px;
      font-size: 40px;
      color: white;
      cursor: pointer;
    }

    /* MODAL PRODUTO */
    .modal-produto {
      display: none;
      position: fixed;
      z-index: 9999;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.88);
      justify-content: center;
      align-items: center;
      padding: 20px;
    }

    .modal-conteudo {
      background: #111;
      border: 2px solid #00ff66;
      border-radius: 20px;
      max-width: 450px;
      width: 100%;
      padding: 25px;
      text-align: center;
      position: relative;
      box-shadow: 0 0 30px rgba(0,255,102,0.35);
      animation: subir 0.3s ease;
    }

    @keyframes subir {
      from {
        opacity: 0;
        transform: translateY(25px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .fechar-modal {
      position: absolute;
      top: 15px;
      right: 20px;
      font-size: 35px;
      color: #00ff66;
      cursor: pointer;
      font-weight: bold;
    }

    .produto-modal-img {
      width: 100%;
      max-height: 300px;
      object-fit: cover;
      border-radius: 15px;
      border: 2px solid #00ff66;
      margin-bottom: 20px;
      cursor: pointer;
    }

    #produtoNome {
      color: #00ff66;
      margin-bottom: 10px;
      font-size: 28px;
    }

    .produto-desc {
      color: #ccc;
      font-size: 15px;
      margin-bottom: 15px;
      line-height: 1.5;
    }

    .produto-preco {
      font-size: 35px;
      color: #00ff66;
      font-weight: bold;
      margin-bottom: 20px;
    }

    .pix-area {
      background: #0b0b0b;
      border: 1px solid #00ff66;
      padding: 18px;
      border-radius: 15px;
    }

    .pix-area h3 {
      color: #00ff66;
      margin-bottom: 12px;
    }

    .pix-chave {
      background: black;
      color: #00ff66;
      padding: 12px;
      border-radius: 10px;
      font-size: 18px;
      font-weight: bold;
      border: 1px solid #00ff66;
      margin-bottom: 12px;
    }

    .btn-pix,
    .btn-whats {
      width: 100%;
      padding: 14px;
      border: none;
      border-radius: 12px;
      font-size: 15px;
      font-weight: bold;
      cursor: pointer;
      margin-top: 10px;
      transition: 0.3s;
    }

    .btn-pix {
      background: #00ff66;
      color: black;
    }

    .btn-pix:hover {
      background: #00cc55;
      transform: scale(1.03);
    }

    .btn-whats {
      background: transparent;
      color: #00ff66;
      border: 2px solid #00ff66;
    }

    .btn-whats:hover {
      background: #00ff66;
      color: black;
      transform: scale(1.03);
    }

    @media (max-width: 900px) {
      .container {
        flex-direction: column;
      }

      .sidebar {
        width: 100%;
      }
    }
  </style>
</head>
<body>

  <!-- TOPO -->
  <div class="topbar">
    <div class="logo">EMF Loja Online</div>

    <div class="search-box">
      <input type="text" placeholder="Buscar caneleiras...">
      <button>Buscar</button>
    </div>

    <div class="menu-top">
      <a href="#">Início</a>
      <a href="#">Promoções</a>
      <a href="#">Mais vendidos</a>
    </div>
  </div>

  <!-- CONTEÚDO -->
  <div class="container">

    <!-- CATEGORIAS -->
    <aside class="sidebar">
      <h3>Categorias</h3>
      <ul>
        <li>⚽ Todas as caneleiras</li>
        <li>🎨 Personalizadas</li>
        <li>🛡️ Profissionais</li>
        <li>🔥 Promoções</li>
      </ul>
    </aside>

    <!-- PRODUTOS -->
    <main class="main">
      <h1 class="titulo-loja">Caneleiras em Destaque</h1>

      <div class="filtros">
        <div class="filtro">Popular</div>
        <div class="filtro">Mais recente</div>
        <div class="filtro">Em destaque</div>
        <div class="filtro">Menor preço</div>
      </div>

      <div class="grid-produtos">

        <!-- PRODUTO 1 -->
        <div class="produto">
          <img src="https://down-br.img.susercontent.com/file/br-11134207-81z1k-mi9ihefttk3ld0.webp" alt="Produto" onclick="abrirModal(this.src)">
          <div class="produto-info">
            <h4>Caneleira Personalizada</h4>
            <div class="avaliacao">★★★★★</div>
            <div class="preco-antigo">R$ 59,90</div>
            <div class="preco">R$ 33,29</div>
            <button class="btn-ver" onclick="abrirProduto('Caneleira Personalizada', 'R$ 33,29', 'https://down-br.img.susercontent.com/file/br-11134207-81z1k-mi9ihefttk3ld0.webp')">Ver Produto</button>
          </div>
        </div>

        <!-- PRODUTO 2 -->
        <div class="produto">
          <img src="https://down-br.img.susercontent.com/file/br-11134207-81z1k-mhzi085eercyd6.webp" alt="Produto" onclick="abrirModal(this.src)">
          <div class="produto-info">
            <h4>Caneleira Super Resistente</h4>
            <div class="avaliacao">★★★★★</div>
            <div class="preco-antigo">R$ 48,00</div>
            <div class="preco">R$ 27,00</div>
            <button class="btn-ver" onclick="abrirProduto('Caneleira Super Resistente', 'R$ 27,00', 'https://down-br.img.susercontent.com/file/br-11134207-81z1k-mhzi085eercyd6.webp')">Ver Produto</button>
          </div>
        </div>

        <!-- PRODUTO 3 -->
        <div class="produto">
          <img src="https://down-br.img.susercontent.com/file/br-11134207-820lv-mlqep7bst1c4c5.webp" alt="Produto" onclick="abrirModal(this.src)">
          <div class="produto-info">
            <h4>Caneleira Box Personalizada</h4>
            <div class="avaliacao">★★★★★</div>
            <div class="preco-antigo">R$ 39,90</div>
            <div class="preco">R$ 30,00</div>
            <button class="btn-ver" onclick="abrirProduto('Caneleira Box Personalizada', 'R$ 30,00', 'https://down-br.img.susercontent.com/file/br-11134207-820lv-mlqep7bst1c4c5.webp')">Ver Produto</button>
          </div>
        </div>

        <!-- PRODUTO 4 -->
        <div class="produto">
          <img src="https://down-br.img.susercontent.com/file/br-11134207-820le-mm5ekbb4qcxydc.webphttps://down-br.img.susercontent.com/file/br-11134207-820le-mm5ekbb4qcxydc.webp" alt="Produto" onclick="abrirModal(this.src)">
          <div class="produto-info">
            <h4>Caneleira Super Leve</h4>
            <div class="avaliacao">★★★★★</div>
            <div class="preco-antigo">R$ 47,90</div>
            <div class="preco">R$ 40,50</div>
            <button class="btn-ver" onclick="abrirProduto('Caneleira Super Leve', 'R$ 40,50', 'https://down-br.img.susercontent.com/file/br-11134207-820le-mm5ekbb4qcxydc.webphttps://down-br.img.susercontent.com/file/br-11134207-820le-mm5ekbb4qcxydc.webp')">Ver Produto</button>
          </div>
        </div>

        <!-- PRODUTO 5 -->
        <div class="produto">
          <img src="https://down-br.img.susercontent.com/file/br-11134207-81z1k-mhwsibgwoikj02.webp" alt="Produto" onclick="abrirModal(this.src)">
          <div class="produto-info">
            <h4>Caneleira Personalizada de Atletas</h4>
            <div class="avaliacao">★★★★★</div>
            <div class="preco-antigo">R$ 64,00</div>
            <div class="preco">R$ 26,99</div>
            <button class="btn-ver" onclick="abrirProduto('Caneleira Personalizada de Atletas', 'R$ 26,99', 'https://down-br.img.susercontent.com/file/br-11134207-81z1k-mhwsibgwoikj02.webp')">Ver Produto</button>
          </div>
        </div>

        <!-- PRODUTO 6 -->
        <div class="produto">
          <img src="https://down-br.img.susercontent.com/file/br-11134207-81z1k-mhzhshk4vs3q58.webp" alt="Produto" onclick="abrirModal(this.src)">
          <div class="produto-info">
            <h4>Caneleira Estilo Pro</h4>
            <div class="avaliacao">★★★★☆</div>
            <div class="preco-antigo">R$ 52,90</div>
            <div class="preco">R$ 29,90</div>
            <button class="btn-ver" onclick="abrirProduto('Caneleira Estilo Pro', 'R$ 29,90', 'https://down-br.img.susercontent.com/file/br-11134207-81z1k-mhzhshk4vs3q58.webp')">Ver Produto</button>
          </div>
        </div>

        <!-- PRODUTO 7 -->
        <div class="produto">
          <img src="https://down-br.img.susercontent.com/file/br-11134207-820lp-mlqep7bshssk2a.webp" alt="Produto" onclick="abrirModal(this.src)">
          <div class="produto-info">
            <h4>CANELEIRA PERSONALIZADA SUPER RESITENTE</h4>
            <div class="avaliacao">★★★★☆</div>
            <div class="preco-antigo">R$ 52,90</div>
            <div class="preco">R$ 30,00</div>
            <button class="btn-ver" onclick="abrirProduto('Caneleira Estilo Pro', 'R$ 30,00', 'https://down-br.img.susercontent.com/file/br-11134207-820lp-mlqep7bshssk2a.webp')">Ver Produto</button>
          </div>
        </div>

        <!-- PRODUTO 8 -->
        <div class="produto">
          <img src="https://down-br.img.susercontent.com/file/br-11134207-81ztc-mj0n36m35hqac2.webp" alt="Produto" onclick="abrirModal(this.src)">
          <div class="produto-info">
            <h4>CANELEIRA PERSONALIZADA D SUA EQUIPE</h4>
            <div class="avaliacao">★★★★☆</div>
            <div class="preco-antigo">R$ 52,90</div>
            <div class="preco">R$ 34,00</div>
            <button class="btn-ver" onclick="abrirProduto('Caneleira Estilo Pro', 'R$ 34,00', 'https://down-br.img.susercontent.com/file/br-11134207-81ztc-mj0n36m35hqac2.webp')">Ver Produto</button>
          </div>
        </div>

        <!-- PRODUTO 9 -->
        <div class="produto">
          <img src="https://down-br.img.susercontent.com/file/br-11134207-81z1k-mhzi5e43agaq6d.webp" alt="Produto" onclick="abrirModal(this.src)">
          <div class="produto-info">
            <h4>CANELEIRA PERSONALIZADA D SUA EQUIPE</h4>
            <div class="avaliacao">★★★★☆</div>
            <div class="preco-antigo">R$ 52,90</div>
            <div class="preco">R$ 30,00</div>
            <button class="btn-ver" onclick="abrirProduto('Caneleira Estilo Pro', 'R$ 30,00', 'https://down-br.img.susercontent.com/file/br-11134207-81z1k-mhzi5e43agaq6d.webp')">Ver Produto</button>
          </div>
        </div>

        <!-- PRODUTO 10 -->
        <div class="produto">
          <img src="https://down-br.img.susercontent.com/file/br-11134207-81z1k-mgtdm5m38qo07b.webp" alt="Produto" onclick="abrirModal(this.src)">
          <div class="produto-info">
            <h4>CANELEIRAS EM BRANCO PARA SUBLIMAÇÃO</h4>
            <div class="avaliacao">★★★★☆</div>
            <div class="preco-antigo">R$ 32,90</div>
            <div class="preco">R$ 18,00</div>
            <button class="btn-ver" onclick="abrirProduto('Caneleira Estilo Pro', 'R$ 18,00', 'https://down-br.img.susercontent.com/file/br-11134207-81z1k-mgtdm5m38qo07b.webphttps://down-br.img.susercontent.com/file/br-11134207-81z1k-mgtdm5m38qo07b.webp')">Ver Produto</button>
          </div>
        </div>

      </div>
    </main>
  </div>

  <!-- MODAL DA IMAGEM -->
  <div class="modal" id="modal" onclick="fecharModal()">
    <span class="fechar">&times;</span>
    <img id="imgModal" src="">
  </div>

  <!-- MODAL DO PRODUTO -->
  <div id="modalProduto" class="modal-produto">
    <div class="modal-conteudo">
      <span class="fechar-modal" onclick="fecharProduto()">&times;</span>

      <img id="produtoImagem" src="" alt="Produto" class="produto-modal-img" onclick="abrirModal(this.src)">

      <h2 id="produtoNome">Nome do Produto</h2>
      <p class="produto-desc">Produto de alta qualidade, confortável e ideal para treino e jogo.</p>

      <div class="produto-preco" id="produtoPreco">R$ 00,00</div>

      <div class="pix-area">
        <h3>💚 Pagamento via Pix</h3>
        <div class="pix-chave" id="pix">11967083179</div>

        <button class="btn-pix" onclick="copiarPix()">📋 Copiar Chave Pix</button>

        <a href="https://wa.me/5511967083179?text=Oi%2C%20acabei%20de%20fazer%20o%20pagamento%20da%20caneleira%20e%20vou%20mandar%20o%20comprovante." target="_blank">
          <button class="btn-whats">📲 Enviar comprovante no WhatsApp</button>
        </a>
      </div>
    </div>
  </div>

  <script>
    function abrirModal(src) {
      document.getElementById("modal").style.display = "flex";
      document.getElementById("imgModal").src = src;
    }

    function fecharModal() {
      document.getElementById("modal").style.display = "none";
    }

    function abrirProduto(nome, preco, imagem) {
      document.getElementById("produtoNome").innerText = nome;
      document.getElementById("produtoPreco").innerText = preco;
      document.getElementById("produtoImagem").src = imagem;
      document.getElementById("modalProduto").style.display = "flex";
    }

    function fecharProduto() {
      document.getElementById("modalProduto").style.display = "none";
    }

    function copiarPix() {
      const pix = document.getElementById("pix").innerText;
      navigator.clipboard.writeText(pix);
      alert("Chave Pix copiada com sucesso!");
    }

    window.onclick = function(event) {
      const modalProduto = document.getElementById("modalProduto");
      if (event.target == modalProduto) {
        fecharProduto();
      }
    }
  </script>

</body>
</html>
