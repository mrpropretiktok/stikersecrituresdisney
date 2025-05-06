<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Stickers Prénom Disney</title>
  <link href="https://fonts.cdnfonts.com/css/waltograph" rel="stylesheet">
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: #fdf6f6;
      color: #333;
      text-align: center;
    }
    header {
      background: #ffc107;
      padding: 20px;
      font-size: 1.8rem;
      font-weight: bold;
    }
    main {
      padding: 40px 20px;
    }
    .disney-preview {
      font-family: 'Waltograph', sans-serif;
      font-size: 48px;
      color: #3b3b98;
      margin-top: 20px;
    }
    input[type="text"] {
      padding: 10px;
      font-size: 1.2rem;
      width: 300px;
      max-width: 90%;
    }
    button {
      padding: 10px 20px;
      font-size: 1rem;
      background-color: #ff4081;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 10px;
    }
    button:hover {
      background-color: #e91e63;
    }
    .example-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
      gap: 20px;
      margin-top: 40px;
    }
    .sticker {
      background: white;
      border: 2px dashed #ddd;
      padding: 20px;
      border-radius: 12px;
      font-family: 'Waltograph', sans-serif;
      font-size: 32px;
      color: #e91e63;
    }
    .cart {
      margin-top: 30px;
      border-top: 1px solid #ccc;
      padding-top: 20px;
    }
    .cart-item {
      font-size: 1.2rem;
      margin: 5px 0;
    }
    .total {
      font-weight: bold;
      margin-top: 10px;
      font-size: 1.2rem;
    }
  </style>
</head>
<body>
  <header>Stickers Prénom - Style Disney ✨</header>
  <main>
    <p>Crée un sticker magique avec le prénom de ton enfant, en écriture Disney !</p>
    <p><strong>Prix : 3 € par sticker – frais de port offerts !</strong></p>

    <input type="text" id="prenomInput" placeholder="Entre un prénom..." oninput="updatePreview()" />
    <div class="disney-preview" id="preview">Emma</div>
    <button onclick="addToCart()">Ajouter au panier</button>

    <div class="cart">
      <h2>🛒 Panier</h2>
      <div id="cartItems">Aucun article pour le moment.</div>
      <div class="total" id="total"></div>
      <button onclick="validerCommande()">Commander</button>
    </div>

    <h2>Exemples :</h2>
    <div class="example-grid">
      <div class="sticker">Emma</div>
      <div class="sticker">Léo</div>
      <div class="sticker">Jade</div>
      <div class="sticker">Noah</div>
    </div>
  </main>

  <script>
    let panier = [];

    function updatePreview() {
      const input = document.getElementById('prenomInput');
      const preview = document.getElementById('preview');
      preview.textContent = input.value || 'Emma';
    }

    function addToCart() {
      const input = document.getElementById('prenomInput').value.trim();
      if (!input) {
        alert("Entre un prénom pour l'ajouter au panier.");
        return;
      }
      panier.push(input);
      afficherPanier();
    }

    function afficherPanier() {
      const cartItems = document.getElementById('cartItems');
      const totalDisplay = document.getElementById('total');
      if (panier.length === 0) {
        cartItems.textContent = 'Aucun article pour le moment.';
        totalDisplay.textContent = '';
        return;
      }
      cartItems.innerHTML = '';
      panier.forEach((item, index) => {
        const div = document.createElement('div');
        div.className = 'cart-item';
        div.textContent = `${item} (Sticker Disney - 3 €)`;
        cartItems.appendChild(div);
      });
      const total = panier.length * 3;
      totalDisplay.textContent = `Total : ${total} € (frais de port offerts)`;
    }

    function validerCommande() {
      if (panier.length === 0) {
        alert("Ton panier est vide !");
        return;
      }
      const total = panier.length * 3;
      const message = encodeURIComponent(`Bonjour, je souhaite commander les stickers suivants :\n- ${panier.join('\n- ')}\n\nTotal à payer : ${total} € (frais de port inclus)`);
      window.location.href = `mailto:j.flinois62@gmail.com?subject=Commande de stickers Disney&body=${message}`;
    }
  </script>
</body>
</html>
